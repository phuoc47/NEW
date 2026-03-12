# CT5 - Build Floral Template bằng .NET MVC

**Deadline:** 3h30

Sử dụng template:  
`https://files.all-free-download.com/downloadfiles/graphic/graphic_7/floral_design_template_6890867.zip`

## Yêu cầu đề bài

- Có 2 bên A, B (2 máy tính).
- Mỗi bên tối thiểu 5 commit.
- Mỗi commit tối thiểu 5 dòng code.
- Tạo 2 conflict và xử lý conflict đúng quy trình.
- Ngôn ngữ chọn: **.NET (ASP.NET Core MVC)**.
- Ráp code HTML/CSS từ template từng phần như dự án thật.
- Khi chấm chỉ tập trung code file giao diện + css.
- Giao diện cuối cùng phải giống template mẫu.

---

## Cấu trúc cuối cùng cần có

| File/Folder | Mô tả |
|---|---|
| `Program.cs` | Cấu hình MVC + static file cho `css/`, `images/` |
| `Controllers/HomeController.cs` | Trả về view trang chính |
| `Views/Home/Index.cshtml` | File giao diện ráp từ template |
| `css/styles.css` | CSS gốc của template |
| `images/` | Ảnh gốc của template |

---

## Quy trình Git bắt buộc

- Không làm trực tiếp trên `main`.
- Tạo `dev` từ `main`.
- Tạo branch task `feature/floral-dotnet` từ `dev`.
- Tất cả thao tác A/B đều trên `feature/floral-dotnet`.
- Luồng mỗi lần làm việc: **Pull -> Code -> Commit -> Push**.
- Xong task: tạo PR `feature/floral-dotnet -> dev` rồi rebase/merge.

---

## Luồng build từ dự án chưa có gì (Dotnet)

### Bước 1 - A (commit A1)

- Tạo repo trống trên remote.
- Clone về máy A.
- Khởi tạo project:

```bash
dotnet new mvc
```

- Commit: `A1 - init dotnet mvc project`
- Push branch `main`.

### Bước 2 - A (commit A2)

- Tạo branch `dev` từ `main`.
- Tạo branch `feature/floral-dotnet` từ `dev`.
- Tạo `Views/Home/Index.cshtml` khung trống (container + các block div chính).
- Commit: `A2 - create empty floral layout skeleton`
- Push `feature/floral-dotnet`.

### Bước 3 - B (commit B1)

- Clone repo về máy B.
- Checkout `feature/floral-dotnet`.
- Pull code mới nhất.
- Ghép phần đầu giao diện: `topLine`, `logoPan`, `menuPan`.
- Commit: `B1 - add top logo menu section`
- Push.

### Bước 4 - A (commit A3)

- Pull từ `feature/floral-dotnet`.
- Ghép phần `header` + slogan ảnh.
- Commit: `A3 - add header section`
- Push.

### Bước 5 - B (commit B2)

- Pull.
- Ghép `leftPan` + `welcome`.
- Commit: `B2 - add left content section`
- Push.

### Bước 6 - A (commit A4)

- Pull.
- Ghép `rightPan` + `featured` + 3 item sản phẩm.
- Commit: `A4 - add right featured section`
- Push.

### Bước 7 - B (commit B3, Conflict #1)

- Pull.
- Sửa `css/styles.css` phần menu/header.
- Đồng thời A đang sửa cùng vùng CSS ở local trước đó.
- B push trước thành công.
- A push sau bị conflict.

**Cách xử lý conflict #1 phía A:**

```bash
git pull origin feature/floral-dotnet
# resolve conflict trong css/styles.css
git add .
git commit -m "A resolve conflict #1 css menu header"
git push origin feature/floral-dotnet
```

### Bước 8 - B (commit B4)

- Pull code mới nhất sau khi A resolve conflict.
- Thêm phần footer trong `Index.cshtml`.
- Commit: `B4 - add footer section`
- Push.

### Bước 9 - A (commit A5, Conflict #2)

- Pull.
- Thêm và chỉnh đường dẫn asset `css/styles.css`, `images/...` trong `Index.cshtml`.
- B cùng lúc chỉnh lại một số dòng đúng vùng đó.
- B push trước, A push sau bị conflict.

**Cách xử lý conflict #2 phía A:**

```bash
git pull origin feature/floral-dotnet
# resolve conflict trong Views/Home/Index.cshtml
git add .
git commit -m "A resolve conflict #2 asset paths in view"
git push origin feature/floral-dotnet
```

### Bước 10 - B (commit B5)

- Pull.
- Rà soát pixel/layout theo template.
- Chỉnh các dòng CSS cuối để giao diện khớp mẫu.
- Commit: `B5 - final css alignment to match template`
- Push.

### Bước 11 - Kết thúc

- A pull lần cuối để đồng bộ.
- Tạo Pull Request: `feature/floral-dotnet -> dev`.
- Rebase/merge theo quy ước nhóm.
- Done.

---

## Bảng commit mẫu (đủ yêu cầu 5 commit mỗi người)

| STT | Người | Commit message |
|---|---|---|
| 1 | A | `A1 - init dotnet mvc project` |
| 2 | A | `A2 - create empty floral layout skeleton` |
| 3 | B | `B1 - add top logo menu section` |
| 4 | A | `A3 - add header section` |
| 5 | B | `B2 - add left content section` |
| 6 | A | `A4 - add right featured section` |
| 7 | B | `B3 - update css menu header` |
| 8 | B | `B4 - add footer section` |
| 9 | A | `A5 - update asset paths in view` |
| 10 | B | `B5 - final css alignment to match template` |

---

## Lệnh build/run dự án Dotnet

```bash
dotnet restore
dotnet build
dotnet run
```

Mở URL local do terminal trả về để kiểm tra giao diện.

---

## Checklist trước khi nộp

- Đúng .NET MVC, có View (`Views/Home/Index.cshtml`).
- Giao diện cuối giống template floral gốc.
- Có đủ 10 commit: A(5) + B(5).
- Có 2 conflict và đã resolve.
- README mô tả đầy đủ luồng từ project trống đến hoàn thiện.
