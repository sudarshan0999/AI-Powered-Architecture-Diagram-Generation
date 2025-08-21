<img width="600" height="400" alt="1" src="https://github.com/user-attachments/assets/c6a960b3-a937-4f12-a76a-a3f3784e4a7a" />

User → Amazon S3 bucket (uploads images/docs) → S3 event triggers AWS Lambda → Lambda calls Amazon SageMaker Endpoint (generate captions/inference) → Lambda calls Amazon Textract (OCR) → Lambda writes captioned images + JSON metadata to Amazon S3 (captions/OCR) → Amazon Kendra indexes S3 content/metadata for search.

![2](https://github.com/user-attachments/assets/9ad3b412-66e2-4047-9375-bdfa1e6a5d0c)


DataSet → Amazon S3 (Source) → AWS Glue DataBrew (clean/transform; writes curated data to S3 Destination) → AWS Glue Crawler (catalog tables) → Amazon Athena (SQL/query) → Amazon SageMaker (train/host) → Amazon QuickSight (dashboards); SageMaker → Amazon CloudWatch (monitoring/logs)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/09f38043-e2a5-4df4-82f9-de3296bc0daf" />

“Video/Image files → Azure Storage → Azure ML pipeline (Jupyter, AML, Inference Cluster, FFmpeg) → Picture files in Data Lake → Orchestrator (Logic App/Function App) → Custom Vision API & Computer Vision API → JSON metadata → WebApp.

<img width="3654" height="2100" alt="image" src="https://github.com/user-attachments/assets/4e7a7ff1-8ab0-4746-9475-a33363980f30" />
Image processing API User UI → Frontend → API Gateway (HTTP POST) → Lambda/Backend API → SageMaker Endpoint (process image) → Lambda (save final output to S3) → API Gateway (return result) → Frontend (display processed image); Optional: S3 → Notify User (send download link)

<img width="689" height="605" alt="image" src="https://github.com/user-attachments/assets/fc9d9b83-a59a-4597-b72e-8e86dc6bd2ea" />
Face-blurring pipeline Users → CloudFront (serve frontend) → S3 Uploads Bucket → Lambda Face‑Blurring Function → Amazon Rekognition (detect faces) → Lambda (blur faces, write result) → S3 Blurred Photos Bucket → CloudFront (serve blurred images) → Users; Optional: Lambda → Amazon SES (email link)

<img width="1400" height="1340" alt="image" src="https://github.com/user-attachments/assets/c1be60c3-0dbe-4e62-956d-292b50808dde" />
LLM-based chatbot app Users → CloudFront → S3 (React app); Auth via Cognito User Pool; Protected by AWS WAF Conversation path: Users → API Gateway (REST) → Lambda (FastAPI) → Amazon Bedrock (Claude 2) → Lambda → API Gateway → Users Streaming/persistence: Users → API Gateway (WebSocket) → Lambda (Publisher) → Amazon SNS → Lambda → DynamoDB (conversation table)

<img width="1427" height="511" alt="image" src="https://github.com/user-attachments/assets/615f9f6e-c5d8-498b-a2df-ac367707fc65" />
VPC web app (two-tier) Users → WAF → CloudFront → Elastic Load Balancer (public subnet) → App Servers (private subnets) → Database (private subnets) Egress: App Servers → NAT Gateway → External AWS/third‑party services

<img width="800" height="308" alt="image" src="https://github.com/user-attachments/assets/73ac2215-ff4c-4077-ac90-8a82e1149163" />
Simple CI/CD to EC2 Developer (commit) → GitHub → GitHub Actions (build/deploy) → Amazon EC2 → Nginx → Live site

<img width="918" height="381" alt="image" src="https://github.com/user-attachments/assets/676064e4-1a92-4a0b-bc68-7fcd57144a4f" />
SageMaker Studio with custom images System Admin → IAM (authenticate) → AWS SSO (set up) → Create SageMaker Studio domain → Assign researchers → Launch EC2 (build images) → Push images to Amazon ECR → Attach images to SageMaker Studio → Jupyter notebooks use custom images

“Video/Image files → Azure Storage → Azure ML pipeline (Jupyter, AML, Inference Cluster, FFmpeg) → Picture files in Data Lake → Orchestrator (Logic App/Function App) → Custom Vision API & Computer Vision API → JSON metadata → WebApp.
