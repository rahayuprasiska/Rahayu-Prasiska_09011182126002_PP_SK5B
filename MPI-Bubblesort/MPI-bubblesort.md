# Langkah-langkah Membuat Cluster MPI

## Sebelum Membuat Cluster MPI

  **1.	Pastikan sudah dalam satu jaringan yang sama untu setiap (Master , Worker, Worker1 dan Worker2)**
  
  **2.	Melakukan upgrade OS**
 
  $ sudo apt update && sudo apt upgrade
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/7d46f494-aed4-4e11-8e4e-019cc6b964dc)
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/833b73b1-e3d0-405d-9377-f8a8836d1d2a)

  **3.	Melakukan penginstalan berikut: net-tools untuk ngecek IP, vim untuk teks editor**
  
  $ sudo apt install net-tools vim
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/63c09930-6297-444e-bf1e-283923fc1d53)
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/f87e5670-6af1-481a-aff5-b70c5c17a1e0)

  **4.	Melakukan pengecekan IP dengan perintah berikut:**
  
  $ Ifconfig
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/c3433601-0461-4c28-91b1-4024fe202a97)

## Steps 1:  to Create an MPI Cluster

  **1.	Konfigurasi hosts file /etc/hosts**
  -	Pada master
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/4c8cae14-cbc0-4581-a8fe-beaf6aaa642d)

  - Pada worker
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/4d631824-e73e-45df-9596-940e7091b53c)

  - Pada worker2
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/a44e4858-2e3a-4ea6-85d6-f4dee80613f9)

  -	Pada worker3
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/183fbe59-a79b-4583-9cde-ccb016e1b3bd)

## Step 2: Create a new user

  Buat user baru di **SERVER** dan **CLIENT**. Nama user harus samo semua di seluruh komputer.
  
  $ sudo adduser <nama user>
  
  $ sudo usermod -aG sudo <nama user>
  
  $ su - <nama user>

  **Server**
  -	Master
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/c9e6b125-9339-462a-b000-d7d611df9710)

  **Client**
  -	Worker
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/cc0b98b2-7ef4-433c-8675-a9a5f4ce8b79)

  -	Worker2
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/9d591c10-f39d-49ae-ba0c-e1637feda4ee)

  -	Worker3
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/821fce12-e023-4869-b158-04edf1e18d6f)

## Step 3: Konfigurasi SSH

  **Setelah membuat dan masuk ke user, lakukan konfigurasi SSH.**

  **1.	Install SSH**
  
  $ sudo apt install openssh-server
  -	Pada master
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/7f42e519-0f6e-4fcf-a2a4-f676a707efb2)

  -	Pada worker
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/151a8b43-9d37-45cd-a9ef-b28ebec02ddd)

  -	Pada worker2
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/4e6b6b98-c3b3-43d0-b425-c0d2af196ad8)

  - Pada worker3
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/c28a5a40-cea6-4948-a4b5-a5f7af5f5ff9)

  **2.	Melakukan pengecekan SSH**
  
  $ ssh <nama user>@<host>

  -	SSH dari Master ke Worker
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/4e44921e-c11d-4475-b0d9-b01cddaac47c)

  -	SSH dari Worker ke Master
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/489fe8fd-2132-452c-8467-5f5908456dba)

  **3.	Generate Keygen**
     
  Lakukan di **SERVER**
  
  $ ssh-keygen -t rsa
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/e4388ec7-cfbe-4f3e-ad98-9d04bf8d387a)

  **4.	Copy key publik ke client**
  
  $ cd .ssh
  
  $ cat id_rsa.pub | ssh <nama user>@<host> "mkdir .ssh; cat >> .ssh/authorized_keys"
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/2b8e5c49-3d7e-4d36-b738-f26bf0107f31)

## Step 4: Konfigurasi NFS

  **1.	Buat shared folder**
  
  $ mkdir cloud

  -	Pada Master
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/d9b7ef28-0c1e-45a3-a1a3-2625b0260c6f)

  -	Pada Worker
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/841e273f-545a-46e5-9a8b-1129211bd767)

  -	Pada Worker2
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/ff7f10b9-5640-472c-bf26-cf7ff22c7652)

  -	Pada Worker3
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/679cd343-47e4-469d-bc19-4292263e82ab)

  **2.	Install NFS Server**

  $ sudo apt install nfs-kernel-server
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/2cefa1c7-2789-440c-8c90-89e8da871e91)

  **3.	Konfigurasi file /etc/exports**
  
  <lokasi shared folder> *(rw,sync,no_root_squash,no_subtree_check)
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/71a8e51f-e9be-4f82-a12e-01a9807261b2)

  $ sudo exportfs -a
  
  $ sudo systemctl restart nfs-kernel-server
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/c187ed04-3b70-42fb-b79a-2253a2b95f28)

  **4.	Install NFS Client**

  $ sudo apt install nfs-common
  
  -	Worker
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/af4836cf-d2c7-4dd9-99c8-9c3a9f548064)

  -	Worker2
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/5141fe7d-3399-4633-9365-d065d6201a12)

  -	Worker3
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/4a16f7d0-a9d5-4354-a27e-8fae2fe47377)

  **5.	Mounting**
  
  $ sudo mount <server host>:<lokasi shared folder di server> <lokasi shared folder di client>

  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/c056095c-8f6e-405d-9946-cc9f68f79728)

## Step 5: MPI

  **1.	Install MPI**

  $ sudo apt install openmpi-bin libopenmpi-dev

  -	Pada Master
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/c54db478-bd27-4c60-b207-9f644f1d741c)

  -	Pada Worker
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/b3634f5a-5947-4cc7-be9e-0adaa98d2574)

  -	Pada Worker2
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/2628d2a0-ed0e-4f25-8e41-0bbb580a03ac)

  -	Pada Worker3
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/3d55a006-9610-45c4-8919-b453f96ae5fb)

  **2.	Testing**

  $ touch test.py
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/1fbfa182-c72a-4f70-99c6-276298ebfad4)

## Step 6: Running MPI programs

  **1.	code program**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/3403e33c-60b7-4335-bd56-e4dc90900d8c)

  **2.	Eksekusi Bubblesort di python3**
  
  -	Menggunakan Worker
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/19a348c2-2f38-4c4c-a2c7-02a3f0e3ff8a)

  -	Menggunakan Master
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/34d02715-0580-4e85-b836-8f69ebca6a74)

  
