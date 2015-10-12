---
title: '[ワードプレス]画像サムネイル作成してURL取得する関数'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/2040
categories:
  - WordPress
tags:
  - WordPress Tip
---
ワードプレスは、サムネイルがない場合は完全なサイズの画像を返します。その後の2000ピクセル建ての画像をHTMLから100pxで表示する悲劇的な事態が起る。画像サムネイルリストであれば、あるページから30MBをダウンロードすることになるかもしれない。

だから、そのような事態を防止するためには、HTML形式で見せてくれるサイズにぴったりのサムネイルをサーバーで生成された後、URLを返しなければならない。それをしてくれる機能だ。引数の値は、添付ファイルの`$post_id`（ワードプレスでは、添付ファイルの情報もpostテーブルに保存されます。）、必要な幅と高さだ。

<pre>function mytory_get_thumb_src($attachment_id, $width, $height){
    $filepath = get_attached_file($attachment_id);
    $upload_path = wp_upload_dir();
    $basedir = $upload_path['basedir'];

    // filepathは$ basedirまで含まれている場合があります。
    $filepath = str_replace($basedir, '', $filepath);
    $fullpath = $basedir . $filepath;
    if( ! is_file($fullpath)){
        return FALSE;
    }
    $pathinfo = pathinfo($fullpath);
    $new_fullpath = $pathinfo['dirname'] . '/' . $pathinfo['filename'] . "-{$width}x{$height}" . '.' . $pathinfo['extension'];
    if( ! is_file($new_fullpath)){
        $image = wp_get_image_editor($fullpath);
        if ( ! is_wp_error( $image ) ) {
            $image-&gt;resize( $width, $height, false );
            $image-&gt;save( $new_fullpath );
        }
    }
    $new_filepath = str_replace($basedir, '', $new_fullpath);
    return $upload_path['baseurl'] . $new_filepath;
}</pre>

また、ワードプレスのイメージを持って作業するときは、`$image = wp_get_image_editor($fullpath)`で始まるをする。この関数は、[WP\_Image\_Editor][1]クラスを返しますが、このクラスは、画像を非常に簡単に編集できるようにAPIが非常によく整理されてています。

 [1]: http://codex.wordpress.org/Class_Reference/WP_Image_Editor