<?php
class produk{
  public $namaBarang, 
         $merk, 
         $ukuranLayar,
         $kapasitas;
         protected $diskon;
         protected $harga;

  public function getCetak(){
    return "$this->merk, (Rp $this->harga)";
  }
  public function __construct($namaBarang="nama barang", $merk="merk", $harga=0, $ukuranLayar="ukuran layar", $kapasitas="kapasitas"){
    $this->namaBarang = $namaBarang;
    $this->merk=$merk;
    $this->harga=$harga;
    $this->ukuranLayar=$ukuranLayar;
    $this->kapasitas=$kapasitas;
  }

    public function cetakInfo(){
        $str="{$this->namaBarang}, {$this->getCetak()}";
        return $str;
    }
    public function setDiskon($diskon){
        $this->diskon=$diskon;
    }
    public function cetakHarga(){
      return $this->harga - ($this->harga * $this->diskon / 100);
    }
}

class handphone extends produk{
  public $ukuranLayar;
  public function __construct ($namaBarang="nama barang", $merk="merk", $harga=0, $ukuranLayar="ukuran layar"){
     parent::__construct($namaBarang, $merk, $harga);
      $this->ukuranLayar=$ukuranLayar;
  }
     
    public function cetakInfo(){
        $str="Laptop: ".parent::getCetak()." | Ukuran Layar: {$this->ukuranLayar}";
        return $str;
    }
}

class ssd extends produk{
   public $kapasitas;
  public function __construct ($namaBarang="nama barang", $merk="merk", $harga=0, $kapasitas="kapasitas"){
     parent::__construct($namaBarang, $merk, $harga);
      $this->kapasitas=$kapasitas;
  }
     
    public function cetakInfo(){
        $str="Aksesoris: ".parent::getCetak()."| Kapasitas: {$this->kapasitas}";
        return $str;
    }
}

$produk1 = new handphone("Asus Zenphone","pro max 1",25000000,"7 inch", "-");
$produk2 = new ssd ("Samsung ","Evo 970",5000000,"1 TB","-");


echo $produk1->cetakInfo();
echo "<br>";
echo $produk2->cetakInfo();
echo "<br>";
echo "<hr>";
$produk1->setDiskon(50);
echo $produk1->cetakHarga();
