# oci

Open Caller ID or oshi (Open Saha Ieu?)

## latar belakang

akhir-akhir ini saya mendapatkan pesan berisi kode OTP untuk sebuah layanan yang tidak pernah saya daftarkan. asumsi
saya adalah entah bagaimana nomor aktif saya tersebar. mempertimbangkan jika untuk brute force nomor telepon valid/aktif
ada 10^10 kombinasi (0-9 dan 10 angka setelah delapan), saya cukup yakin jika asumsi saya terdengar lebih masuk akal.

![https://s3.edgy.social/0x0/F17F1B8A-EC0C-4E99-ADE0-7B3722B7A285.jpeg](https://s3.edgy.social/0x0/F17F1B8A-EC0C-4E99-ADE0-7B3722B7A285.jpeg)

di sisi lain, tidak jarang juga mendapatkan telepon masuk dari nomor tidak dikenal, yang katanya, ini bagian dari adulting: dari
penawaran asuransi sampai kartu kredit.

sudah ada beberapa layanan yang cukup populer digunakan untuk mencari tahu identitas pengguna nomor telepon,
seperti Truecaller dan Getcontact jika menyebut dua. cara kerja singkatnya saya rasa cukup sederhana: pengguna mengunggah daftar
kontak nya—nama dan nomor telepon—ke server mereka, and that's it, ig. berdasarkan data tersebut, pengguna A bisa tahu jika nama
"Farhan KKN" di kontak nya adalah "Farhan Oli Samping" di kontak pengguna lain.

untuk beberapa pengguna, mereka baik-baik saja tidak mengetahui hal-hal detail. namun untuk beberapa pengguna lain, mereka cukup
peduli. pertanyaan yang mungkin remeh seperti _"untuk apa **lagi** data tersebut digunakan?"_ mungkin terbesit di benak mereka,
dan membaca halaman "Kebijakan Privasi" ataupun "Ketentuan Layanan" tidak terlalu memuaskan. di era informasi seperti saat ini, pendekatan
"kumpulkan data sebanyak mungkin lalu pikirkan nanti" (meminjam istilah "retrospective decryption") mungkin cukup lumrah, apalagi hari
ini AI menjadi keren yang mana terus menjadi berguna bila diberikan informasi khususnya yang aktual.

saat sedang berjalan-jalan santai saya kepikiran _"bagaimana jika ada layanan serupa namun dari komunitas, oleh komunitas, untuk komunitas?"_
lalu terbitlah repo ini.

## dump

saya kepikiran seperti kombinasi [hibp](https://haveibeenpwned.com/) dan [project honeypot](https://www.projecthoneypot.org/) untuk fondasi:

### nomor telepon

- menyimpan data nomor telepon tanpa menyimpan data nomor telepon
- layanan tidak perlu tahu jika user A mencari nomor telepon 081xxxxxx666
- hibp menggunakan k-anonimity: user submit prefix hash, hibp mengembalikan hash dengan prefix tersebut, lalu pencocokkan terjadi di klien
- mungkin dapat diterapkan juga untuk kasus ini?

### trust/spam score

- bagian tersulit, khususnya dalam konteks "urun-daya"
- ["credit system"](https://dri.es/solving-the-maker-taker-problem) nya Drupal menarik, tapi apakah relevan?
- moderasi???

### threat actor

- user punya daftar nomor telepon dan ingin mengetahui apa pemilik siapa untuk kepentingan lain (harvest)
- karena hash one-way, umumnya rentan dengan brute force (rainbow table). sha2 cukup resistant terhadap tabel pelangi meskipun tanpa garam but who knows 
- tapi karena generally ini reverse lookup, dan tujuan utamanya adalah itu, what could possibly go wrong?
- yea rate-limit is not invited here btw
- bagaimana dengan "gb reputasi"?
- what could possibly go wrong?

## prinsip

- community-first
- privacy-centric
- open source
- open data
