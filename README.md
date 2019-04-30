# Вывод комментариев WordPress

```php
<div class="row">

  <?php
    $args = array(
      'number' => 10,
      'orderby' => 'comment_date',
      'order' => 'DESC',
      'type' => '', // только комментарии, без пингов и т.д...
    );

    if( $comments = get_comments( $args ) ){

      foreach( $comments as $comment ){
        $comm_link = get_comment_link( $comment->comment_ID ); // может быть тяжелый запрос ...
        $comm_short_txt = mb_substr( strip_tags( $comment->comment_content ), 0, 50 ) .'...';
      ?>

      <div class="col-lg-12 item">
        <div class="row">
          <div class="col-lg-1 col-2">
            <div class="ava"><?php echo get_avatar( $comment, 54 ); ?></div>
          </div>
          <div class="col-lg-11 col-10">
            <?php echo '<div class="uname">'. $comment->comment_author . '</div>'; ?>
            <?php echo '<div class="comment">'. $comm_short_txt . '</div>'; ?>
          </div>
        </div>
      </div>

      <?php
      }
    };
    ?>

</div>
```
