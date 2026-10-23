# python-docker-image-comparison
Build and Compare Lightweight vs Heavyweight Docker Images for a Python Application
# Python Docker Image Comparison: Alpine vs Standard

Build the same Python application on two base images, then compare sizes, run both containers, test them and document the results.
 Step 1: Create the GitHub repository
1. On GitHub, click **New repository**, name it `python-docker-image-comparison`, and create it.
2. Clone it and enter the folder:
   ```bash
   https://github.com/SHARMIgithubrit/python-docker-image-comparison
   cd python-docker-image-comparison
 
Step 2: Create the project files
Final structure:
```
python-docker-image-comparison/
├── app.py
├── requirements.txt
├── Dockerfile.alpine
├── Dockerfile.standard
└── README.md

 Step 4: Build both images
docker build -t app1:v1 -f Dockerfile.alpine.
docker build -t app2:v2 -f Dockerfile.standard .

Step 5: Compare image sizes
docker images
  docker build -t app1:v1 -f Dockerfile.alpine.--format '{{.1808}}'
  docker build -t app2:v2 -f Dockerfile.standard .--format '{{.2390}}'

Calculate the reduction:

Size reduction (%) = ((Standard size - Alpine size) / Standard size) * 100
                   = ((2390-1808))/2390 *100 =23.351   
```
Step 6: Run the containers
```bash
docker run -d --name Application1 -p 8080:80 app1:v1
docker run -d --name Application2 -p 8081:8000 app2:v2

 Step 7: Test the application
Alpine container:
```bash
 http://localhost:8080
 http://localhost:80
```
Standard container:
```bash
 http://localhost:8001/
 http://localhost:8000/health
```

Step 8: Verify container status and logs
```bash
docker ps
docker logs containerID
```
Step 9: Clean up
```bash
docker ps - copy the container id
docker stop container_id -stop
docker rm container_id - delete 
docker images - list the docker images
docker rmi docker_image_id - delete

 Step 10: Document the results and submit
1. Fill in the Results tables below with your actual output.
2. Commit and push the README:
   git add README.md
   git commit -m "Completed"
   git push


