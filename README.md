
# Django Web App + OTP

## Setup Instructions

### 1. Install Python
Ensure Python3 is installed on your machine. You can verify by running:
```bash
python3 --version
```

### 2. Create a Virtual Environment
Isolate your project environment to avoid conflicts. Choose one of the following methods:

#### Using Anaconda/Miniconda:
```bash
conda create --name forageenv python=3.9
conda activate forageenv
```

#### Using venv:
```bash
python3 -m venv forageenv
source forageenv/bin/activate
```

### 3. Set Up the Django Project
Unzip the `mysite.zip` file and navigate to the project directory:
```bash
cd mysite

# Install required Python modules
pip3 install -r requirements.txt

# Synchronize the database
python3 manage.py migrate

# Create the site admin user
python3 manage.py createsuperuser
# Follow the prompts to set the username, email, and password

# Run the web application
python3 manage.py runserver
```

### 4. Install and Configure Django OTP
Follow the [Django OTP installation docs](https://django-otp-official.readthedocs.io/en/stable/overview.html#installation) and modify `settings.py` to use the `otp_totp` plugin. Modify the necessary variables.

Stop the running server:
```bash
Ctrl-C
```

Modify `settings.py` and then run:
```bash
python3 manage.py migrate
python3 manage.py runserver
```

### 5. Modify urls.py
Add the following after the existing import statements in `urls.py`:
```python
from django_otp.admin import OTPAdminSite
admin.site.__class__ = OTPAdminSite
```

### 6. Add a Device in Admin
Navigate to `http://localhost:8000/admin/` and add a device. Click on the QR code to copy the link and answer the final quiz question. Replace the `secret` value with `<SECRET>`.

## Additional Notes
For a detailed discussion on setting up Django, follow [this tutorial](https://docs.djangoproject.com/en/3.2/intro/tutorial01/).

## Repository
[Link to the GitHub repository](https://github.com/your-username/django-otp-webapp)

