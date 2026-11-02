# Practical 10: Docker Containerization of the Iris ML Application
# 1. Objective
To containerize the Iris machine learning application using Docker, package a trained model, expose HTTP endpoints for predictions, and verify the application using health checks.
# 2. Tools and Technologies
Docker Desktop with the Linux container engine
Python 3.11
scikit-learn
pandas, NumPy and joblib
Python http.server
Git and GitHub
# 3. Implementation
The application uses a multi-stage Dockerfile.
# Builder stage
Installs the pinned Python dependencies.
Reads data/processed/iris_features.csv.
Trains a Random Forest classifier.
Saves the model and label encoder.
# Runtime stage
Copies the installed Python packages and trained model from the builder.
Copies src/serve.py.
Exposes port 8000.
Configures a Docker health check using /health.
# 4. HTTP Endpoints
# Method	Endpoint	Purpose
GET	/health	Checks application health
POST	/predict	Predicts an Iris species from the required features
The prediction request contains four original Iris measurements and three engineered numeric features: sepal_area, petal_area, and sepal_to_petal_length_ratio.
# 5. Build and Run
Build the image:
docker build -t iris-classifier:v1 .
Start the container:
docker run -d --name iris-classifier-container -p 8000:8000 iris-classifier:v1
Check container status:
docker ps
# 6. Testing and Results
# Health check
Request:
curl http://localhost:8000/health
Observed response:
{"status": "healthy"}
# Valid prediction
For the sample Iris measurements, the application returned:
{"prediction": "setosa", "probabilities": [1.0, 0.0, 0.0]}
# Invalid request
A request missing required features returned HTTP 400 Bad Request and identified the missing fields.
# 7. Conclusion
The Iris ML application was successfully containerized using a multi-stage Docker build. The model was trained during the image build, the HTTP server returned a valid prediction, and invalid input was handled with an appropriate client error. The health endpoint responded successfully.
# 8. Cleanup
Stop and remove the running container when finished:
docker stop iris-classifier-container
docker rm iris-classifier-container
The Docker image can be retained locally for future use.