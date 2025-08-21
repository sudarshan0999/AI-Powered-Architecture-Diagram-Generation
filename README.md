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

<img width="881" height="511" alt="image" src="https://github.com/user-attachments/assets/5e50cf88-e725-4e5b-98f7-2df3869f50b1" />
Image Q&A with Bedrock, OpenSearch, S3, DynamoDB User/API client → Amazon API Gateway → AWS Lambda → store image in Amazon S3 → Amazon Bedrock (VLM, e.g., Sonnet) → Amazon Bedrock (Titan Text Embeddings) → Amazon OpenSearch Service (vector search; index prebuilt via SageMaker notebook) → Amazon Bedrock (LLM, generate answer) → AWS Lambda (persist query/response in DynamoDB) → Amazon API Gateway → User

<img width="869" height="412" alt="image" src="https://github.com/user-attachments/assets/11556150-5fcf-4e6f-8ef2-a76d3a0f46f8" />
Static site + Bedrock text generation Users → Amazon S3 (static pages hosting) Text request: Users → Amazon API Gateway → AWS Lambda → Amazon Bedrock → AWS Lambda → Amazon API Gateway → Users

<img width="1111" height="741" alt="image" src="https://github.com/user-attachments/assets/ea073a68-8389-45cc-b7e0-fb905a897f9e" />
Chatbot with Lex + Bedrock Knowledge Bases Static UI: Amazon S3 (web UI assets) → Amazon CloudFront → Users Chat: Users → GenAI Chat UI → Amazon Lex → Knowledge Bases for Amazon Bedrock → Amazon S3 (documents) → Knowledge Bases → Amazon Lex → GenAI Chat UI → Users

<img width="1201" height="629" alt="image" src="https://github.com/user-attachments/assets/bc037976-35f8-4969-80fb-210201b0358a" />
Amplify web app with Bedrock and Polly TTS Users → CloudFront → S3 (app assets, managed by Amplify) Auth: Users ↔ Amazon Cognito Q&A: Users → API Gateway → AWS Lambda → Amazon Bedrock → AWS Lambda → API Gateway → Users Optional TTS: UI text → Amazon Polly → audio to S3 → CloudFront → Users

<img width="1538" height="710" alt="image" src="https://github.com/user-attachments/assets/dbfc3add-3366-4757-9c44-341ce8ef7d3d" />
Streaming chat with Bedrock and DynamoDB memory Users ↔ AWS Lambda (response streaming) ↔ Amazon Bedrock (model streaming) ; Lambda ↔ Amazon DynamoDB (chat memory)

<img width="1588" height="1172" alt="image" src="https://github.com/user-attachments/assets/7f38c0e4-476b-4c2b-9aa6-ce459b527f25" />
Multi-endpoint GenAI (text→image, text→text, RAG with embeddings) Setup: SageMaker notebook → deploy endpoints (Text-to-Image, Text-to-Text, Text-to-Embedding) Users → Amplify front end → Cognito (login) → API Gateway → VPC links a) Text-to-Image: API Gateway → Lambda (text→image) → SageMaker Endpoint (text→image) → Lambda → Users b) Text-to-Text: API Gateway → Lambda (text→text) → SageMaker Endpoint (text→text) → Lambda → Users c) RAG: API Gateway → Lambda (RAG search) → SageMaker Endpoint (text→embedding) → Amazon OpenSearch (embeddings index) → Lambda → Users Indexing pipeline: Documents → Fargate indexing job → SageMaker Endpoint (text→embedding) → Amazon OpenSearch (embeddings index)

<img width="1280" height="553" alt="image" src="https://github.com/user-attachments/assets/3f3d71f3-6284-46e0-9140-e7f454fe37e5" />

<img width="772" height="338" alt="image" src="https://github.com/user-attachments/assets/1480662f-504b-44f7-b76d-1f9e2d642f76" />

<img width="1400" height="959" alt="image" src="https://github.com/user-attachments/assets/0efb30d9-509c-4fa4-9674-d56ad2e80676" />

<img width="990" height="591" alt="image" src="https://github.com/user-attachments/assets/1f6723d2-03ee-4952-9285-238fa4d39145" />

<img width="871" height="501" alt="image" src="https://github.com/user-attachments/assets/961c4966-47be-4f07-ae54-82cbe96964a6" />

<img width="1206" height="533" alt="image" src="https://github.com/user-attachments/assets/67deb442-2a24-4d5f-b281-ba243a26be87" />
