GitHub **removed password authentication** for Git operations over HTTPS and now requires **personal access tokens (PATs) or SSH keys** instead.

### **How to Fix GitHub Authentication Issue**
Since password authentication is deprecated, you need to **use a personal access token (PAT)** or **SSH key authentication**.

#### **Solution 1: Use Personal Access Token (Recommended)**
1. **Generate a Personal Access Token (PAT)**
   - Go to **GitHub Settings** → **Developer Settings** → **Personal Access Tokens** → **Tokens (classic)**
     [Click here to generate a token](https://github.com/settings/tokens)
   - Click **Generate new token (classic)**.
   - Select **repo** permissions for full repository access.
   - Set an expiration date or make it **no expiration**.
   - Copy the generated token (you won’t be able to see it again).

2. **Use PAT Instead of Password**
   When pushing changes, instead of using your **GitHub password**, use the **generated token**:
   ```sh
   git push https://<your-username>@github.com/itoroukpe/Git.git
   ```
   - Example:
     ```sh
     git push https://itoroukpe@github.com/itoroukpe/Git.git
     ```
   - When prompted for a **password**, enter the **PAT instead**.

3. **Save Credentials to Avoid Entering PAT Every Time**
   - Configure Git to save your credentials:
     ```sh
     git config --global credential.helper store
     ```
   - Push again, and it will store the token for future authentication.

---

#### **Solution 2: Use SSH Authentication (Alternative)**
If you prefer using **SSH keys instead of PAT**, follow these steps:

1. **Generate an SSH Key (if not already done)**
   ```sh
   ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
   ```
   - Press **Enter** to save in the default location (`~/.ssh/id_rsa`).
   - Add a passphrase for security (optional).

2. **Add SSH Key to GitHub**
   - Copy the SSH key:
     ```sh
     cat ~/.ssh/id_rsa.pub
     ```
   - Go to **GitHub Settings** → **SSH and GPG keys** → **New SSH Key**
   - Paste the key and save.

3. **Update Git Remote URL**
   ```sh
   git remote set-url origin git@github.com:itoroukpe/Git.git
   ```
   - Now push using SSH:
     ```sh
     git push -u origin main
     ```

---

#### **Final Steps: Verify Connection**
To confirm that authentication is set up correctly, run:
```sh
git remote -v
```
If you set up SSH, test the connection:
```sh
ssh -T git@github.com
```

