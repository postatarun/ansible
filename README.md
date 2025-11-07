---
# 🧩 Ansible Automation Playbooks

This repository contains a collection of **Ansible playbooks** to automate common Linux system administration and DevOps tasks such as **user management**, **Apache web server setup**, and **Docker installation**.

These playbooks are designed to simplify provisioning, configuration, and management of servers — making infrastructure automation faster, repeatable, and error-free.

---

## 📁 Folder Structure
```

ansible/
├── ansible.cfg
├── inventory/
│   └── hosts.ini
├── playbooks/
│   ├── user-create.yml
│   ├── apache-install.yml
│   ├── docker-setup.yml
│   ├── loop1.yml
│   └── loop-vars.yml
├── roles/
│   ├── common/
│   ├── apache/
│   └── docker/
└── group_vars/

````

---

## 🚀 Getting Started

### ✅ Prerequisites
- **Ansible** v2.14 or newer  
- **Python 3.8+**  
- SSH access to target hosts  
- Properly configured **inventory** and **ansible.cfg**

### 📦 Clone the Repository
```bash
git clone https://github.com/<your-username>/ansible.git
cd ansible
````

### ⚙️ Inventory Setup

Edit your inventory file (`inventory/hosts.ini`):

```ini
[node1]
192.168.56.101 ansible_user=ansible ansible_ssh_private_key_file=~/.ssh/id_rsa

[node2]
192.168.56.102 ansible_user=ansible
```

---

## ▶️ Run a Playbook

### Create Users

```bash
ansible-playbook -i inventory/hosts.ini playbooks/user-create.yml
```

### Install Apache Web Server

```bash
ansible-playbook -i inventory/hosts.ini playbooks/apache-install.yml
```

### Deploy Docker Engine

```bash
ansible-playbook -i inventory/hosts.ini playbooks/docker-setup.yml
```

> 💡 Use `-K` if `become: true` is used for privilege escalation:
>
> ```bash
> ansible-playbook -i inventory/hosts.ini playbooks/docker-setup.yml -K
> ```

---

## 🧠 Example: Loop Variable Playbook

```yaml
---
- name: Create multiple users from a variable file
  hosts: node1
  vars_files:
    - loop-vars.yml
  tasks:
    - name: Create users
      ansible.builtin.user:
        name: "{{ item }}"
        state: present
      loop: "{{ users_lists }}"
```

**loop-vars.yml**

```yaml
users_lists:
  - akash
  - ravi
  - mathan
  - suresh
  - chand
```

---

## 🔧 Useful Commands

```bash
ansible --version
ansible-inventory -i inventory/hosts.ini --list
ansible-playbook --syntax-check playbooks/apache-install.yml
ansible -m ping all -i inventory/hosts.ini
```

---

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome!
Feel free to fork this repository and raise a pull request.

---

## 📜 License


---

## 🧰 Tags

`#ansible` `#devops` `#automation` `#infrastructure-as-code` `#linux` `#docker` `#apache`

---

### ✨ Author

**Arun Bansal**
🔗 [GitHub](https://github.com/postatarun) | 💼 Senior DevOps Engineer

---
