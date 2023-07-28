1. 在 Models/Movie.cs 文件中為 Movie 模型添加一個新的屬性 public string Distributor { get; set; }
2. 對數據庫進行遷移以更新數據結構在 Package Manager Console 中執行以下指令：
    Add-Migration AddDistributor
    Update-Database
3. 在 Controllers/MoviesController.cs 中更新我們的 Create 和 Edit 方法，以便能接受新的發行公司參數:
    public ActionResult Edit([Bind(Include = "ID,Title,ReleaseDate,Genre,Price,Rating,Distributor")] Movie movie)
    public async Task<IActionResult> Edit(int id, [Bind("ID,Title,ReleaseDate,Genre,Price,Distributor")] Movie movie)
4. 在 Create 和 Edit 的視圖中添加一個新的輸入欄位，使得用戶能輸入或編輯發行公司。在 Views/Movies/Create.cshtml 和 Views/Movies/Edit.cshtml 中添加以下
    <div class="form-group">
        <label asp-for="Distributor" class="control-label"></label>
        <input asp-for="Distributor" class="form-control" />
        <span asp-validation-for="Distributor" class="text-danger"></span>
    </div>
5. 在 Views/Movies/Index.cshtml 和 Views/Movies/Details.cshtml 中添加以下程式碼以顯示發行公司
    <td>
        @Html.DisplayFor(modelItem => item.Distributor)
    </td>
