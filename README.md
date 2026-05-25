<?php
session_start();

if (!isset($_SESSION['dangnhap'])) {
    header("Location: ../login.php");
    exit();
}

include "../includes/ketnoi.php";

$ds = mysqli_query($conn, "SELECT * FROM congvan ORDER BY id DESC");
?>

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Công văn đã đăng</title>

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>

<body class="bg-light">

<nav class="navbar navbar-dark bg-primary">
    <div class="container-fluid">
        <a href="../dashboard.php" class="navbar-brand">← Trang quản trị</a>
        <a href="../logout.php" class="btn btn-danger">Đăng xuất</a>
    </div>
</nav>

<div class="container mt-4">

    <h2 class="mb-4">CÔNG VĂN ĐÃ ĐĂNG</h2>

    <?php while ($row = mysqli_fetch_assoc($ds)) { ?>

        <div class="card shadow border-0 mb-3">
            <div class="card-body">
                <h4 class="text-primary">
                    <?php echo $row['tieude']; ?>
                </h4>

                <p><b>Số công văn:</b> <?php echo $row['socongvan']; ?></p>
                <p><b>Loại:</b> <?php echo $row['loaicongvan']; ?></p>
                <p><b>Ngày gửi:</b> <?php echo $row['ngaygui']; ?></p>

                <hr>

                <p><?php echo $row['noidung']; ?></p>
            </div>
        </div>

    <?php } ?>

</div>

</body>
</html>



