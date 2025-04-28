Customer Service Chatbot

This is a simple customer service chatbot built with Python, Flask, and NLTK, deployed on Firebase App Hosting. It handles basic customer queries such as return policies and order tracking.

Setup Instructions





Clone the Repository:

git clone <your-repository-url>
cd customer-service-chatbot



Create a Virtual Environment:

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate



Install Dependencies:

pip install -r requirements.txt



Run the Application Locally:

python app.py



Test the Chatbot Locally: Use a tool like Postman or curl to send POST requests to http://localhost:8080/chat with a JSON body:

{"message": "What is your return policy?"}

Deploying to Firebase App Hosting





Install Firebase CLI:

npm install -g firebase-tools



Login to Firebase:

firebase login



Initialize Firebase Hosting: Run in the project directory:

firebase init hosting





Select your Firebase project.



Choose Firebase App Hosting as the hosting type.



Use . as the public directory.



Configure as a single-page app: No.



Set up automatic builds: No (unless using GitHub Actions).



Deploy to Firebase:

firebase deploy --only hosting



Test the Deployed Chatbot: Send POST requests to https://<your-firebase-app>.web.app/chat with a JSON body:

{"message": "What is your return policy?"}

Troubleshooting





NLTK Data Download Error: If you encounter an error like [nltk_data] Error loading punkt, ensure the app has internet access during runtime. The app downloads the 'punkt' tokenizer on demand. To pre-download:

import nltk
nltk.download('punkt')



Firebase Build Error: If the build fails (e.g., step exited with non-zero status: 1):





Check Google Cloud Build logs in the Cloud Console for details.



Ensure all files (app.py, requirements.txt, firebase.json) are in the repository root.



Verify the Firebase project has the necessary permissions:

gcloud projects add-iam-policy-binding <project-id> \
    --member=serviceAccount:<project-number>@cloudbuild.gserviceaccount.com \
    --role=roles/cloudbuild.builds.builder
gcloud projects add-iam-policy-binding <project-id> \
    --member=serviceAccount:<project-number>@cloudbuild.gserviceaccount.com \
    --role=roles/artifactregistry.writer
gcloud projects add-iam-policy-binding <project-id> \
    --member=serviceAccount:<project-number>@cloudbuild.gserviceaccount.com \
    --role=roles/firebasehosting.admin



Port Configuration: Firebase expects the app to listen on the PORT environment variable (default 8080). This is configured in app.py.

Project Structure





app.py: Main application file containing the chatbot logic and Flask server.



requirements.txt: Lists the required Python packages.



firebase.json: Firebase Hosting configuration.



Dockerfile: Custom build configuration for Firebase App Hosting.



README.md: Project documentation.



.gitignore: Excludes unnecessary files from version control.

Contributing

Feel free to fork this repository and submit pull requests for improvements.

License

MIT License
