<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Clear Storm - Giza</title>

<style>
body {
    font-family: Arial;
    direction: rtl;
    background: #f4f6f9;
    text-align: center;
}

h1 {
    background: #0d6efd;
    color: white;
    padding: 15px;
}

.search-box {
    margin: 20px;
}

input {
    padding: 10px;
    width: 300px;
    font-size: 16px;
}

button {
    padding: 10px 20px;
    background: #198754;
    color: white;
    border: none;
    cursor: pointer;
}

table {
    width: 90%;
    margin: 20px auto;
    border-collapse: collapse;
    background: white;
}

th, td {
    border: 1px solid #ddd;
    padding: 10px;
}

th {
    background: #0d6efd;
    color: white;
}
</style>
</head>

<body>

<h1>موقع كلير ستورم - الجيزة</h1>

<div class="search-box">
    <input type="text" id="searchInput" placeholder="اكتب الاسم أو الرقم للبحث">
    <button onclick="searchData()">بحث</button>
</div>

<table>
    <thead>
        <tr>
            <th>الاسم</th>
            <th>رقم الهاتف</th>
            <th>الرقم القومي</th>
            <th>تاريخ الميلاد</th>
        </tr>
    </thead>
    <tbody id="resultTable">
    </tbody>
</table>

<script>

// ضع بياناتك هنا (يمكنك تحويل ملف الاكسل إلى JSON)
const data = [
    {
        name: "مثال اسم",
        phone: "01000000000",
        nationalId: "00000000000000",
        birthDate: "1/1/2000"
    }
];

// البحث
function searchData() {
    let input = document.getElementById("searchInput").value.toLowerCase();
    let table = document.getElementById("resultTable");
    table.innerHTML = "";

    let results = data.filter(item =>
        item.name.toLowerCase().includes(input) ||
        item.phone.includes(input) ||
        item.nationalId.includes(input)
    );

    if(results.length === 0){
        table.innerHTML = "<tr><td colspan='4'>لا توجد نتائج</td></tr>";
        return;
    }

    results.forEach(item => {
        table.innerHTML += `
        <tr>
            <td>${item.name}</td>
            <td>${item.phone}</td>
            <td>${item.nationalId}</td>
            <td>${item.birthDate}</td>
        </tr>`;
    });
}

</script>

</body>
</html>
