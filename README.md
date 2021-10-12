# mvc-list-view
Film listemizi repository üzerinden gelen bilgileri oluşturuyoruz.<br>

HomeContoller.cs içinde ki Index methodumuzu oluşturuyoruz.<br>
Repository den aldığı Moviesleri gönderiyoruz.<br>
`using MovieApp.Models;` namespace eklemeyi unutmuyoruz Repository görünür olması için.
```javascript
public IActionResult Index()
        {
            return View(Repository.Movies);
        }
```
![](https://i.resim.host/ZSmM0I.png)
_movies.cshtml sayfamızı oluşturuyoruz.<br>
Bu sayfanın bir modele ihtiyacı var. Modelin liste olduğunu bildiğimiz için IEnumerable kullanıyoruz.
```javascript
@model IEnumerable<Movie>

@foreach (var movie in Model)
{
    <div class="card" style="margin-bottom:5px;">
        <div class="row no-gutters">
            <div class="col-md-3">
                <img class="card-img-top" src="~/img/@movie.ImageUrl" alt="@movie.Description">
            </div>
            <div class="col-md-9">
                <div class="card-body">
                    <h5 class="card-title">@movie.Name</h5>
                    <p class="card-text">@movie.Description</p>
                    <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
                </div>
            </div>
        </div>
    </div>
}
```
![](https://i.resim.host/97ymVq.png)

Index.cshtml sayfamızı oluşturuyoruz.<br>
HomeController Index methodunda  repository içinden aldığı moviesleri gönderiyor.<br>
HomeController dan aldığımız listeyi index sayfamıza sonrasında indexten ise movies sayfamıza gönderiyoruz.

```javascript
@{
    ViewData["Title"] = "Home Page";
}
@model IEnumerable<Movie>

<div class="row">
    <div class="col-md-3">
        @Html.Partial("_menu")
    </div>
    <div class="col-md-9">
        <partial name="_movies" model="Model" />
    </div>
</div>

```

TagHelper ile ` <partial name="_movies" model="Model" /> ` Modelimizi olduğu gibi movies sayfamıza gönderiyoruz.

![](https://i.resim.host/aBEekw.png)
