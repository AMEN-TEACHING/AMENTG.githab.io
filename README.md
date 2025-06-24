import os
from zipfile import ZipFile

# Create folder structure
site_dir = "suy-amen-website"
os.makedirs(site_dir, exist_ok=True)

# File content dictionary
files = {
    "index.html": "<!DOCTYPE html> ...",  # Paste the full HTML content here
    "topics.html": "<!DOCTYPE html> ...",
    "tutorials.html": "<!DOCTYPE html> ...",
    "resources.html": "<!DOCTYPE html> ...",
    "contact.html": "<!DOCTYPE html> ...",
    "login.html": "<!DOCTYPE html> ...",
    "styles.css": "body { font-family: 'Poppins', sans-serif; } ...",  # CSS content
}

# Save files
for filename, content in files.items():
    with open(os.path.join(site_dir, filename), "w", encoding="utf-8") as f:
        f.write(content)

# Create ZIP file
zip_name = f"{site_dir}.zip"
with ZipFile(zip_name, 'w') as zipf:
    for file in os.listdir(site_dir):
        zipf.write(os.path.join(site_dir, file), arcname=file)

print(f"Website packaged as: {zip_name}")
