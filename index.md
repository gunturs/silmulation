# Pratikum Teknik Modulasi
## Pertemuan 8: Membuat halaman untuk pengambilan tiket
Pertemuan sebelumnya kita sudah berhasil membuat laman Dashboard dimana laman tersebut menampilkan petugas yang aktif dan no Antrian yang sedang dilayani.
![Image]( dasboard.PNG )

Selanjutnya kita akan membuat laman Nasabah untuk mengambil Nomor Antrian 
![Image]( nasabah.PNG )


dalam hal ini langkah pertama yang kita lakukan adalah merancang tabel baru yang diberi nama nasabah dengan struktur seperti dibawah ini:
![Image]( tabel_nasabah.PNG )

lalu isi tabel tersebut dengan nilai awal<br>
![Image]( nasabah_awal.PNG )

Buat sebuah controller dengan nama Nasabah.php dengan syntaks sebagai berikut
```php
<?php
defined('BASEPATH') or exit('No direct script access allowed');

class Nasabah extends CI_Controller
{
    public function __construct()
    {
        parent::__construct();
    }
    public function index()
    {
        $data['nasabah'] = $this->db->get('nasabah')->result_array();
        $this->load->view('header', $data);
        $this->load->view('nasabah');
        $this->load->view('footer');
    }
    public function teller($antri = '')
    {
        $data = [
            "teller" => $antri + 1
        ];
        $this->db->update('nasabah', $data);
        $data['nasabah'] = $this->db->get('nasabah')->result_array();
        $this->load->view('tiket_teller', $data);
        redirect("nasabah");
    }
    
}
```
`file diatas diletakan dalam folder applicaton/controller`
ada 2 function yang harus diperhatikan pada program diatas yaitu index dan teller<br>
```
 public function index()
    {
        $data['nasabah'] = $this->db->get('nasabah')->result_array();
        $this->load->view('header', $data);
        $this->load->view('nasabah');
        $this->load->view('footer');
    }
```

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```
