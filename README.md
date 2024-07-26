# WordPress Theme Deployment

This repository contains the WordPress theme for [TheBestBlogEver.co](https://thebestblogever.co) and uses GitHub Actions for automated deployment to a web host via FTP.

## Setup Instructions

### Repository Structure

wordpress/
.github/
workflows/
php.yml
my-theme/
functions.php
style.css
main.js
(other theme files)

### Deployment Workflow

The deployment workflow is triggered on every push to the `main` branch. It checks out the code, sets up PHP, and deploys the theme files to the specified FTP server.

### Configuration

The workflow file `.github/workflows/php.yml` includes the FTP credentials directly for demonstration purposes. For better security, use GitHub Secrets.

```yaml
name: Deploy WordPress Theme

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Setup PHP
      uses: shivammathur/setup-php@v2
      with:
        php-version: '7.4'

    - name: Sync files via FTP
      uses: SamKirkland/FTP-Deploy-Action@4.1.0
      with:
        ftp-server: 'ftp://your-ftp-server.com'
        ftp-username: 'your-ftp-liyamflx'
        ftp-password: 'your-ftp-password'
        local-dir: './my-theme'
        remote-dir: '/path-to-your-wordpress/wp-content/themes/my-theme'

    - name: Finalize deployment
      run: echo "Deployment complete!"
git clone https://github.com/liyamflx/your-repo.git
cd your-wordpress
git add .
git commit -m "Initial commit"
git push origin main
Steps to Use
Clone the Repository:

sh
Copy code
git clone https://github.com/yourusername/your-repo.git
cd your-repo
Modify FTP Credentials:

Update the ftp-server, ftp-username, and ftp-password in the .github/workflows/php.yml file.
Push Changes to GitHub:

sh
Copy code
git add .
git commit -m "Initial commit"
git push origin main
Monitor Deployment:

Go to the Actions tab in your GitHub repository.
Monitor the workflow to ensure it runs successfully and deploys your theme to the web host.
Note
For production environments, it is highly recommended to use GitHub Secrets to store sensitive information like FTP credentials.

License
This project is licensed under the MIT License - see the LICENSE file for details.

markdown
Copy code

### Steps to Complete:

1. **Create Repository and Files:**
   - Create a new GitHub repository.
   - Add your theme files under a directory (e.g., `my-theme`).
   - Add the `.github/workflows/php.yml` file.
   - Add the `README.md` file.

2. **Commit and Push:**
   - Commit all changes and push them to the `main` branch of your repository.

3. **Monitor the Workflow:**
   - Go to the **Actions** tab in your GitHub repository.
   - Monitor the workflow to ensure it runs successfully and deploys your theme to the web host.

By following these steps, you should be able to set up your GitHub Actions workflow and README file to document and automate the deployment of your WordPress theme. If you encounter any issues or need further assistance, feel free to ask!
