# Petunjuk Ujian:

## Alat dan Bahan
- Virtualbox, boleh di Linux Host atau Windows Host
- Internet
- SSH Client untuk mengakses Control Node

## Template
**Root User:**
- username: root
- password: bismillah

**User:**
- username: user
- password: bismillah

**Yang Sudah Terinstall:**
- SSH Server (root sudah bisa login)
- 3 Adapter Network

## Struktur Praktikum
**Controller Node:**
- NAT
- Internal Network: intnet (IP: 10.10.30.10/24)
- Host-only Network: (IP: 192.168.56.10/24)
- Terinstall Ansible

**Target Node 1:**
- NAT
- Internal Network: intnet (IP: 10.10.30.1/24)
- Host-only Network: (IP: 192.168.56.11/24)
- Untuk Web Server

**Target Node 2:**
- NAT
- Internal Network: intnet (IP: 10.10.30.2/24)
- Host-only Network: (IP: 192.168.56.12/24)
- Untuk Database Server

## Langkah Praktikum
1. Setup VM di virtualbox sesuai dengan Struktur Praktikum diatas
2. **Setting IP Address** pada Controller Node, Target Node 1, dan Target Node 2
3. Install **Ansible** di Controller Node
4. Pastikan **Controller Node dapat terhubung** ke Target Node 1 dan Target Node 2 menggunakan SSH & SSH-keygen
5. Copy Paste **inventory.yml** dan **sites.yml** ke Controller Node
6. Sesuaikan dengan kebutuhan
7. Jalankan **Ansible Playbook**

## Target Praktikum
1. **KKM:** Bisa Melakukan Ansible Ping `ansible -i inventory.ini all -m ping`
2. **76-85:** Bisa mengakses tes html di alamat `http://192.168.56.11/htmltest.html`
3. **>86:** Bisa mengakses tes database di alamat `http://192.168.56.11/dbtest.html`

## Model Ujian
- Open book, open internet
- Laporan Sesuai Template

## Command Snippets:
- `ssh-keygen -t rsa -b 4096` -> membuat ssh-keypair
- `ssh-copy-id user@10.10.30.1` -> mengcopy ssh-keypair ke target node
- `ssh-copy-id user@10.10.30.2` -> mengcopy ssh-keypair ke target node
- `sudo apt install ansible ansible-core` -> menginstall ansible
- `ansible -i inventory.ini all -m ping` -> menjalankan ansible ping
- `ansible-playbook -i inventory.ini sites.yaml --ask-become-pass` -> menjalankan ansible playbook
