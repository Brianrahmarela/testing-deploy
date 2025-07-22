Cara clone dan menjalankan API di lokal:

- Clone repo yang ingin di download: https://github.com/Brianrahmarela/testing-deploy
- Di terminal jalankan: git clone https://github.com/Brianrahmarela/testing-deploy
- Setelah terbentuk folder testing-deploy, cd testing-deploy
- Kemudian ketik code .
- Setelah vs code berjalan. di terminal jalankan: go run main.go
- Buka postmant/browser, akses url: http://localhost:3000/v1/api/users

Step by step deployment ke VPS
- Buat repository projek di github
- di github Tambahkan konfigurasi SSH pada tab Setting -> Secrets and variables -> Actions, lalu klik New repository secret.
- SSH_HOST, berisi alamat host server. contoh: 203.175.11.199,
SSH_USER, berisi user server. contoh: student,
SSH_PRIVATE_KEY, berisi private key yang cocok dengan public key pada server. 
- Sesuaikan script pada file .github/workflows/deploy.yml
- Buat commit baru pada project, lalu push ke branch utama (disini kita menggunakan branch main).
- Login ke server via SSH dengan perintah: ssh student@203.175.11.199
- Masuk ke dalam folder/direktori yang sudah ditetapkan dengan perintah cd nama-folder
- Setelah itu kita clone repository agar server dapat menjalankan script git pull pada ci/cd 
- copy file .env.example dengan nama .env menggunakan perintah berikut: cp .env.example .env
- kemudian buat perubahan di local, git add, git commit, git push
- saat di push github akan deploy otomatis ke vps

Link API endpoint publik yang sudah dideploy:
http://203.175.11.199:8002/v1/greeting
http://203.175.11.199:8002/v1/about
http://203.175.11.199:8002/v1/api/users