<html>
    <head>
        <meta charset = "UTF-8" />
    </head>
    <body>
        <h1>Bài tập 4</h1>
        <h2>a)</h2>
        <?php 
        $arSanPham = array(
                        array(
                            'id_sp'     => '1',
                            'ten'       => 'Đồng hồ thông minh',
                            'gia'       => '159000',
                            'so_luong'  => '5',
                        ),
                        array(
                            'id_sp'     => '2',
                            'ten'       => 'Gậy tự sướng',
                            'gia'       => '19000',
                            'so_luong'  => '10',
                        ),
                        array(
                            'id_sp'     => '3',
                            'ten'       => 'Pin sạc dự phòng',
                            'gia'       => '259000',
                            'so_luong'  => '5',
                        ),
                        array(
                            'id_sp'     => '4',
                            'ten'       => 'Heo đỡ điện thoại',
                            'gia'       => '9000',
                            'so_luong'  => '30',
                        ),
                        array(
                            'id_sp'     => '5',
                            'ten'       => 'Kẹp điện thoại đuôi khỉ',
                            'gia'       => '25000',
                            'so_luong'  => '10',
                        )
                    );
        ?>
        <table border = "1px" style="border-collapse: collapse"> 
            <tr>
                <th>id_sp</th>
                <th>ten</th>
                <th>gia</th>
                <th>so_luong</th>
            </tr>
            <?php 
                foreach($arSanPham as $value){
            ?>
            <tr style="text-align: center">
                <td><?php echo $value['id_sp']; ?></td>
                <td><?php echo $value['ten']; ?></td>
                <td><?php echo number_format($value['gia']); ?></td>
                <td><?php echo $value['so_luong']; ?></td>
            </tr>
            <?php
                }
            ?>
        </table>
        <h2>b)</h2>
        <?php
            echo '<h3>sản phẩm có giá > 20000:</h3>';
            foreach($arSanPham as $value){
                if($value['gia'] > 20000){
                    echo "id_sp: {$value['id_sp']}, ten: {$value['ten']}, gia: {$value['gia']}, so_luong: {$value['so_luong']} <br/>";
                }else{
                    
                }
            };
        ?>
        <h2>c)</h2>
        <?php
            foreach($arSanPham as $key => $value){
                $thanh_tien = $value['gia'] * $value['so_luong'];
                $arSanPham[$key]['thanh_tien'] = $thanh_tien;
            }
            
        ?>
        <table border = "1px" style="border-collapse: collapse"> 
            <tr>
                <th>id_sp</th>
                <th>ten</th>
                <th>gia</th>
                <th>so_luong</th>
                <th>thanh_tien</th>
            </tr>
            <?php 
                foreach($arSanPham as $value){
            ?>
            <tr style="text-align: center">
                <td><?php echo $value['id_sp']; ?></td>
                <td><?php echo $value['ten']; ?></td>
                <td><?php echo number_format($value['gia']); ?></td>
                <td><?php echo $value['so_luong']; ?></td>
                <td><?php echo number_format($value['thanh_tien']); ?></td>
            </tr>
            <?php
                }
            ?>

        </table>
        <h2>d)</h2>
        <?php
            foreach($arSanPham as $key => $value){
                if($value['so_luong'] >= 30){
                    $discount = $value['thanh_tien'] * 0.1;
                    
                }elseif($value['so_luong'] >= 10){
                    $discount =$value['thanh_tien'] * 0.05;
                }else{
                    $discount = 0;
                }
                $thanh_tien = $value['thanh_tien'] - $discount;
                $arSanPham[$key]['thanh_tien'] = $thanh_tien;
            }
        ?>
        <table border = "1px" style="border-collapse: collapse"> 
            <tr>
                <th>ten</th>
                <th>thanh_tien</th>
            </tr>
            <?php 
                foreach($arSanPham as $value){
            ?>
            <tr style="text-align: center">
                <td><?php echo $value['ten']; ?></td>
                <td><?php echo number_format($value['thanh_tien']); ?></td>
            </tr>
            <?php
                }
            ?>
        </table>
        <!-- //////////////////////////////////////////////////// -->
        <h2>e)</h2>
        <?php 
            $count = 0;
            foreach($arSanPham as $value){
                if($value['gia'] >= 25000){
                    $count++;
                }
            }
            echo 'có ' .$count . ' sản phẩm có giá 25000 trở lên.';
        ?>
    </body>
</html>