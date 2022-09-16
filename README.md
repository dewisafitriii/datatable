# datatable
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Latihan 1</title>
    <style>
        #simpan{
            padding: 10px;
            width: 100%;
            background: linear-gradient(#017E71, #00C2AE);
            border-radius: 10px;
            color: white;
            border-width: 0px;
        }
        #simpan:hover{
            color: white;
            background: linear-gradient(#04626f, #01CBDF);
        }
    </style>
    <link rel="stylesheet" href="Datatables/datatables.min.css">
</head>
<body>
    <input type="hidden" id="id" autocomplete="off">
    <table style="font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif; font-size: 17px;" width="50%" align="center">
        <tr>
            <td colspan="8" align="center"><h3>Input Data ke Tabel</h3></td>
        </tr>
        <tr>
            <td>Nama</td>
            <td><input style="width: 90%; padding: 5px; border-radius: 10px;"type="text" name="nama" placeholder="Masukkan Nama"/></td>
            <td>Kelas</td>
            <td> <input style="width: 90%; padding: 5px; border-radius: 10px;"type="text" name="kelas" placeholder="Masukkan Kelas"/></td>
        </tr>
        <tr>
            <td>Alamat</td>
            <td><input style="width: 90; padding: 5px; border-radius: 10px;"type="text" name="alamat" placeholder="Masukkan Alamat"/></td>
            <td>Nomor Handphone</td>
            <td><input style="width: 90%; padding: 5px; border-radius: 10px;"type="text" name="no_hp" placeholder="Masukkan No HP"/></td>
        </tr>
        <tr>
            <td colspan="8" align="center"><button id="simpan">Simpan Data</button></td>
            td colspan="8" align="center"><button id="hapus" style="display:none; padding:10px; background-color: red;color: white";>Hapus Data</button></td>
        </tr>
    </table>
    
    <table id="contoh" class="display">
        <thead>
            <tr>
                <th width="10%">No</th>
                <th width="25%">Nama</th>
                <th width="25%">Kelas</th>
                <th width="20%">Alamat</th>
                <th width="20%">No HP</th>
            </tr>
        </thead>
    </table>
<script src="DataTables/jQuery-3.6.0/jquery-3.6.0.min.js"></script>
<script src="DataTables/datatables.min.js"></script>  
    <script>
    
      var table = $("#contoh").DataTable({
                responsive : true,
                select: true,
                
       });

         table.on('select', function(){
            $("#id").val(table.rows(".selected").data().toArray()[0][0])
            $("input[name=nama]").val(table.rows(".selected").data().toArray()[0][1]);
            $("input[name=kelas]").val(table.rows(".selected").data().toArray()[0][2]);
            $("input[name=alamat]").val(table.rows(".selected").data().toArray()[0][3]);
            $("input[name=no_hp]").val(table.rows(".selected").data().toArray()[0][4]);
            $("#simpan").html("Ubah Data");
            $("#hapus").show();
         });

         tabel.on('deselect', function(){
            $("#simpan").html("Simpan Data");
            $("input[name=nama]").val(null);
            $("input[name=kelas]").val(null);
            $("input[name=alamat]").val(null);
            $("input[name=no_hp]").val(null);
            $("#hapus").hide();
         });

       var no = 1;    
        $("#simpan").click(function(){
            var nama =   $("input[name=nama]").val();
            var kelas =  $("input[name=kelas]").val();
            var alamat = $("input[name=alamat]").val();
            var no_hp =  $("input[name=no_hp]").val();
            var id   = $("#id").val();
             
            if (id.length > 0){
                table.row(id-1).data(
                   [id,nama,kelas.alamat,no_hp]
                ).draw();

            } else{
                table.row.add(
                     [no,nama, kelas,alamat,no_hp,]
            ).draw(false);
            no++;
            }
            $("#simpan").html("Simpan Data");
            $("input[name=nama]").val(null);
            $("input[name=kelas]").val(null);
            $("input[name=alamat]").val(null);
            $("input[name=no_hp]").val(null);
       });


       // $(function(){
            //var data = [
            //    ["1","Rizkia","K2","Mabar","08113333555555"],
            //    ["2","Nuari","K2","Nobar","08778888999999"],
            //];

           // var data = [];

           // for (let i = 0; i < 5; i++){
                //data.push([i]);
                //for (let j = 0; j < 5; j++){
                    //data[i].push(j);
              //  }
           // }

           // $("#contoh").DataTable({
               // responsive : true,
           // });

    </script>
  
</body>
</html>
