# pagination php

```php
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
# pagination jquery

```javascript
var data = [
  {
    id: 1,
    name: "Koke",
    position: "CM",
  },
  {
    id: 2,
    name: "Diego Godin",
    position: "CB",
  },
  {
    id: 3,
    name: "Lodi",
    position: "LB",
  },
  {
    id: 4,
    name: "Saul Niguez",
    position: "CM",
  },
  {
    id: 5,
    name: "Luis Suarez",
    position: "ST",
  },
  {
    id: 6,
    name: "C.Ronaldo",
    position: "ST",
  },
  {
    id: 7,
    name: "Yannick F. Carrasco",
    position: "LM",
  },
  {
    id: 8,
    name: "Angle Correa",
    position: "RM",
  },
  {
    id: 9,
    name: "Y.Oblak",
    position: "GK",
  },
  {
    id: 10,
    name: "Miranda",
    position: "CB",
  },
  {
    id: 11,
    name: "Jao Felix",
    position: "ST",
  },
  {
    id: 12,
    name: "Gabi",
    position: "CM",
  },
  {
    id: 13,
    name: "Tiago",
    position: "CM",
  },
  {
    id: 14,
    name: "Saul Niguez",
    position: "CM",
  },
  {
    id: 15,
    name: "Luis Suarez",
    position: "ST",
  },
  {
    id: 16,
    name: "C.Ronaldo",
    position: "ST",
  },
  {
    id: 17,
    name: "Yannick F. Carrasco",
    position: "LM",
  },
  {
    id: 18,
    name: "Angle Correa",
    position: "RM",
  },
  {
    id: 19,
    name: "Y.Oblak",
    position: "GK",
  },
  {
    id: 20,
    name: "Miranda",
    position: "CB",
  },
  {
    id: 21,
    name: "Koke",
    position: "CM",
  },
  {
    id: 22,
    name: "Diego Godin",
    position: "CB",
  },
  {
    id: 23,
    name: "Lodi",
    position: "LB",
  },
  {
    id: 24,
    name: "Saul Niguez",
    position: "CM",
  },
  {
    id: 25,
    name: "Luis Suarez",
    position: "ST",
  },
];

var page = 1;
var totalpage = 0;

$(document).ready(() => {
  render();
});

function render() {
  var html = "";
  for (var i = (page - 1) * 3; i < page * 3; i++) {
    if (i < data.length) {
      html += `
              <tr>
                  <td>${data[i].id}</td>
                  <td>${data[i].name}</td>
                  <td>${data[i].position}</td>
              </tr>
          `;
    }
  }
  $("#tbody").html(html);

  totalpage = Math.ceil(data.length / 3);

  var pagination_html = "";

  if (totalpage > 0) {
    if (page > 1) {
      pagination_html = `<li class="page-item" onclick="back_page()"><a class="page-link" href="#">Previous</a></li>`;
    }
    if (page > 3) {
      pagination_html += `<li class="page-item" id="page1" onclick="current_page(1)"><a class="page-link" href="#">1</a></li>`;
      pagination_html += `<li class="page-item"><a class="page-link">...</a></li>`;
    }
    if (page - 2 > 0) {
      pagination_html += `<li class="page-item" id="page${
        page - 2
      }" onclick="current_page(${page - 2})"><a class="page-link" href="#">${
        page - 2
      }</a></li>`;
    }
    if (page - 1 > 0) {
      pagination_html += `<li class="page-item" id="page${
        page - 1
      }" onclick="current_page(${page - 1})"><a class="page-link" href="#">${
        page - 1
      }</a></li>`;
    }
    pagination_html += `<li class="page-item active" id="page${page}" onclick="current_page(${page})"><a class="page-link" href="#">${page}</a></li>`;
    if (page + 1 < totalpage + 1) {
      pagination_html += `<li class="page-item" id="page${
        page + 1
      }" onclick="current_page(${page + 1})"><a class="page-link" href="#">${
        page + 1
      }</a></li>`;
    }
    if (page + 2 < totalpage + 1) {
      pagination_html += `<li class="page-item" id="page${
        page + 2
      }" onclick="current_page(${page + 2})"><a class="page-link" href="#">${
        page + 2
      }</a></li>`;
    }
    if (page < totalpage - 2) {
      pagination_html += `<li class="page-item"><a class="page-link">...</a></li>`;
      pagination_html += `<li class="page-item" id="page${totalpage}" onclick="current_page(${totalpage})"><a class="page-link" href="#">${totalpage}</a></li>`;
    }
    if (page < totalpage) {
      pagination_html += `<li class="page-item" onclick="next_page()"><a class="page-link" href="#">Next</a></li>`;
    }
  }
  $("#pagination").html(pagination_html);
}

function next_page() {
  if (page != totalpage) {
    page++;
    render();
  }
}

function back_page() {
  if (page != 1) {
    page--;
    render();
  }
}

function current_page(cu_page) {
  page = cu_page;
  render();
}
```
