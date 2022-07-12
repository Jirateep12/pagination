# paginations

```
<nav class="d-flex justify-content-center mt-3" aria-label="Page navigation example">
  <ul class="pagination">
    <?php
    $test = $pdo->test(); // ตัวอย่าง
    (isset($_GET['p'])) ? $page = $_GET['p'] :  $page = 1; // get page
    $total_page = ceil($pr_result / 20); // set page = 20
    ?>
    <?php
    if ($total_page > 0) {
    ?>
      <?php if ($page > 1) { ?>
        <li class="page-item"><a class="page-link" href="./../../../../../../test/page/<?= $page - 1; ?>/">Previous</a></li>
      <?php } ?>
      <?php if ($page > 3) { ?>
        <li class="page-item"><a class="page-link" href="./../../../../../../test/page/1/">1</a></li>
        <li class="page-item"><a class="page-link">...</a></li>
      <?php } ?>
      <?php if ($page - 2 > 0) { ?>
        <li class="page-item"><a class="page-link" href="./../../../../../../test/page/<?= $page - 2 ?>/"><?= $page - 2 ?></a></li>
      <?php } ?>
      <?php if ($page - 1 > 0) { ?>
        <li class="page-item"><a class="page-link" href="./../../../../../../test/page/<?= $page - 1 ?>/"><?= $page - 1 ?></a></li>
      <?php } ?>
      <li class="page-item active"><a class="page-link" href="./../../../../../../test/page/<?= $page ?>/"><?= $page ?></a></li>
      <?php if ($page + 1 < $total_page + 1) { ?>
        <li class="page-item"><a class="page-link" href="./../../../../../../test/page/<?= $page + 1 ?>/"><?= $page + 1 ?></a></li>
      <?php } ?>
      <?php if ($page + 2 < $total_page + 1) { ?>
        <li class="page-item"><a class="page-link" href="./../../../../../../test/page/<?= $page + 2 ?>/"><?= $page + 2 ?></a></li>
      <?php } ?>
      <?php if ($page < $total_page - 2) { ?>
        <li class="page-item"><a class="page-link">...</a></li>
        <li class="page-item"><a class="page-link" href="./../../../../../../test/page/<?= $total_page ?>/"><?= $total_page ?></a></li>
      <?php } ?>
      <?php if ($page < $total_page) { ?>
        <li class="page-item"><a class="page-link" href="./../../../../../../test/page/<?= $page + 1 ?>/">Next</a></li>
      <?php } ?>
    <?php
    }
    ?>
  </ul>
</nav>
```
