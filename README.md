# CV Website - Muztabir Bakhtear

## Description
A personal CV website showcasing professional profile, resume, and downloadable CV. This static website includes profile photo, professional information, and a downloadable PDF resume.

## Live Demo
🔗 [View Live Website](https://your-bucket-name.s3.amazonaws.com/index.html)

## Files Included
- `index.html` - Main website page
- `IMG_4645.jpg` - Profile photo
- `Cv-main.pdf` - Downloadable CV/Resume
- `README.md` - This file

## Features
- Clean and professional design
- Responsive layout
- Profile photo display
- Downloadable CV in PDF format
- Hosted on AWS S3 for reliable access

## How to Use

### Local Development
1. Clone this repository:
   ```bash
   git clone https://github.com/mustabirapurbo/cv-website-muztabir.git
   ```
2. Navigate to the project directory:
   ```bash
   cd cv-website-muztabir
   ```
3. Open `index.html` in your web browser to view locally

### Deployment to AWS S3

#### Prerequisites
- AWS Account
- AWS CLI installed and configured

#### Steps to Deploy

1. **Create an S3 Bucket**
   ```bash
   aws s3 mb s3://your-unique-bucket-name
   ```

2. **Configure Bucket for Static Website Hosting**
   ```bash
   aws s3 website s3://your-unique-bucket-name --index-document index.html
   ```

3. **Update Bucket Policy for Public Access**
   Create a file named `bucket-policy.json` with:
   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "PublicReadGetObject",
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::your-unique-bucket-name/*"
       }
     ]
   }
   ```
   Apply the policy:
   ```bash
   aws s3api put-bucket-policy --bucket your-unique-bucket-name --policy file://bucket-policy.json
   ```

4. **Upload Files to S3**
   ```bash
   aws s3 cp index.html s3://your-unique-bucket-name/
   aws s3 cp IMG_4645.jpg s3://your-unique-bucket-name/
   aws s3 cp Cv-main.pdf s3://your-unique-bucket-name/
   ```

5. **Access Your Website**
   Your website will be available at:
   ```
   http://your-unique-bucket-name.s3-website-[region].amazonaws.com
   ```

#### Alternative: Using AWS Console

1. Log into AWS Console and navigate to S3
2. Create a new bucket with a unique name
3. Enable "Static website hosting" in bucket properties
4. Set `index.html` as the index document
5. Update bucket permissions to allow public read access
6. Upload all files (`index.html`, `IMG_4645.jpg`, `Cv-main.pdf`)
7. Access the website using the S3 static website endpoint

## Customization

To customize the website for your own use:
1. Replace `IMG_4645.jpg` with your own profile photo
2. Replace `Cv-main.pdf` with your own CV/Resume
3. Edit `index.html` to update personal information, styling, and content
4. Update the live demo link in this README after deployment

## Technologies Used
- HTML5
- CSS (embedded or linked)
- AWS S3 for hosting

## Author
**Muztabir Bakhtear**

## License
This project is available for personal use.

---

*Note: Remember to update the demo link and bucket name placeholders after deploying to AWS S3.*
