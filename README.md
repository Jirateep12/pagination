### # php pdo oop 😎

```php
<nav class="d-flex justify-content-center mt-3" aria-label="Page navigation example">
  <ul class="pagination">
    <?php
    public function data($database)
    {
      $pdo = new DB_con();
      $result = $pdo->connect()->prepare("SELECT * FROM " . $database . "");
      $result->execute();
      $result = $result->rowCount();
      return $result;
    }
    
    $result = $pdo->data("database");
    (isset($_GET['page'])) ? $page = $_GET['page'] :  $page = 1; // get page
    $total_page = ceil($result / 2); // set page = 2
    ?>
      <?php if ($total_page > 0) { ?>
        <li class="page-item <?= ($page > 1) ? "" : "disabled" ?>"><a class="page-link" href="<?= $page - 1; ?>">Previous</a></li>
        <?php if ($page > 3) { ?>
          <li class="page-item"><a class="page-link" href="/page/1/">1</a></li>
          <li class="page-item"><a class="page-link">...</a></li>
        <?php } ?>
        <?php if ($page - 2 > 0) { ?>
          <li class="page-item"><a class="page-link" href="<?= $page - 2 ?>"><?= $page - 2 ?></a></li>
        <?php } ?>
        <?php if ($page - 1 > 0) { ?>
          <li class="page-item"><a class="page-link" href="<?= $page - 1 ?>"><?= $page - 1 ?></a></li>
        <?php } ?>
        <li class="page-item active"><a class="page-link" href="<?= $page ?>"><?= $page ?></a></li>
        <?php if ($page + 1 < $total_page + 1) { ?>
          <li class="page-item"><a class="page-link" href="<?= $page + 1 ?>"><?= $page + 1 ?></a></li>
        <?php } ?>
        <?php if ($page + 2 < $total_page + 1) { ?>
          <li class="page-item"><a class="page-link" href="<?= $page + 2 ?>"><?= $page + 2 ?></a></li>
        <?php } ?>
        <?php if ($page < $total_page - 2) { ?>
          <li class="page-item"><a class="page-link">...</a></li>
          <li class="page-item"><a class="page-link" href="<?= $total_page ?>"><?= $total_page ?></a></li>
        <?php } ?>
        <li class="page-item <?= ($page < $total_page) ? "" : "disabled" ?>"><a class="page-link" href="<?= $page + 1 ?>">Next</a></li>
      <?php } ?>
  </ul>
</nav>
```
### # javascript / jquery 😎

```javascript
var data = [
  {
    name: "Ms. Russel Stokes",
    birthday: "2022-03-21T13:03:29.133Z",
    phone: "1-401-061-4740",
    zip: "35696",
    city: "Lake Lauryn",
    email: "Wilhelm5@hotmail.com",
  },
  {
    name: "Viviane Schmeler",
    birthday: "2022-03-27T13:22:42.431Z",
    phone: "(140) 397-8791 x086",
    zip: "41462",
    city: "Milobury",
    email: "Myrtie_Hilll@gmail.com",
  },
  {
    name: "Jairo McKenzie",
    birthday: "2022-02-07T08:23:01.612Z",
    phone: "(969) 635-5849 x44088",
    zip: "83721-0489",
    city: "Ashleyton",
    email: "Jannie_Leffler76@yahoo.com",
  },
  {
    name: "Tristin Durgan",
    birthday: "2022-06-23T22:43:15.582Z",
    phone: "(189) 559-9823 x275",
    zip: "79124",
    city: "Lake Ashley",
    email: "Laurie_Hilpert16@gmail.com",
  },
  {
    name: "Vince Christiansen DVM",
    birthday: "2021-09-20T02:28:51.022Z",
    phone: "(709) 147-1273 x899",
    zip: "83367-8888",
    city: "New Michaela",
    email: "Fredy_Dicki34@hotmail.com",
  },
  {
    name: "Jayden Barrows",
    birthday: "2022-06-01T08:55:01.021Z",
    phone: "069-088-4749",
    zip: "80683",
    city: "South Jacky",
    email: "Hugh.Kirlin10@gmail.com",
  },
  {
    name: "Bertrand Jacobson II",
    birthday: "2022-05-24T04:38:57.795Z",
    phone: "222-176-9440",
    zip: "32806",
    city: "Port Alexandria",
    email: "Chadrick14@gmail.com",
  },
  {
    name: "Laisha Heathcote",
    birthday: "2022-05-20T14:19:17.292Z",
    phone: "1-423-340-1596 x6611",
    zip: "93608-5700",
    city: "Padbergport",
    email: "Kenyon_Waelchi@yahoo.com",
  },
  {
    name: "Alfred Lang",
    birthday: "2021-12-03T09:19:18.038Z",
    phone: "394.047.4303 x66836",
    zip: "16814",
    city: "Larsonton",
    email: "Caesar_Schiller36@yahoo.com",
  },
  {
    name: "Nathaniel Tremblay",
    birthday: "2022-01-13T23:14:36.586Z",
    phone: "(181) 267-1841",
    zip: "93072",
    city: "Orrinfurt",
    email: "Calista43@yahoo.com",
  },
];

var page = 1;
var totalpage = 0;

$(document).ready(() => {
  render();
});

function render() {
  var html = "";
  for (var i = (page - 1) * 2; i < page * 2; i++) {
    if (i < data.length) {
      html += `
        <tr>
            <td>${data[i].name}</td>
            <td>${data[i].birthday}</td>
            <td>${data[i].phone}</td>
            <td>${data[i].zip}</td>
            <td>${data[i].city}</td>
            <td>${data[i].email}</td>
        </tr>
    `;
    }
  }
  $("#tbody").html(html);

  totalpage = Math.ceil(data.length / 2);

  var pagination_html = "";

  if (totalpage > 0) {
    pagination_html = `<li class="page-item ${
      page > 1 ? "" : "disabled"
    }" onclick="back_page()"><a class="page-link" href="#">Previous</a></li>`;
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
    pagination_html += `<li class="page-item ${
      page < totalpage ? "" : "disabled"
    }" onclick="next_page()"><a class="page-link" href="#">Next</a></li>`;
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
