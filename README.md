# gcp_vertex_ai

Steps for Building end to end pipeline for Face Recognition Dataset

Prerequisites
  1. A Google Cloud Platform (GCP) project with billing enabled.
  1. A Kaggle account to download the face recognition dataset.
  2. 
Instructions
  1. Download Dataset: Download the "Face Recognition Dataset" from Kaggle (https://www.kaggle.com/datasets/cybersimar08/face-recognition-dataset).

  2. Create Storage Bucket
       a. In your GCP Console, navigate to Cloud Storage.
       b. Create a new bucket in the "us-central" region (important for AutoML compatibility).

  3. Upload Data: Upload the downloaded face recognition dataset folder to your Cloud Storage bucket.

  4. Create Vertex AI Notebook:
        a. Go to the Vertex AI Workbench section of your GCP Console.
        b. Create a new user-managed notebook.

  5. Prepare Data:
        a. Open the notebook you created.
        b. Install any required libraries (e.g., pandas, google-cloud-storage).
        c. Write code to:
             a. List images in your Cloud Storage bucket.
             b. Extract labels from the image paths or folder structure.
             c. Create a CSV file with columns for image paths (gcs_uri) and labels.

  6. Create Vertex AI Dataset:
        a. Navigate to Vertex AI Datasets.
        b. Create a new Image dataset with "Single-label classification" task type.
        c. Import data using the "Upload from Google Cloud Storage (with CSV manifest)" option, selecting your CSV file.

  7.Train AutoML Model:
        a. Start the AutoML training process.
        b. Allocate 8 node hours for training.

  8.Deploy Model:
        a. Upon training completion, deploy the best model to an Endpoint.

  9.Perform Inference
        a.Use the notebook or Python code with the Vertex AI SDK to send images to your endpoint for face recognition predictions.
