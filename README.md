# Go Expert Auction API

This project is a clone of the [GoExpert Auction API](https://github.com/devfullcycle/labs-auction-goexpert) repository, with added functionality to automatically close auctions after a defined time.

## How to Run the Project Locally

### 1. Clone the repository

Clone this repository to your local machine:

```
git clone https://github.com/jordanoluz/goexpert-auction-api.git
```

### 2. Navigate to the project directory

Change into the project directory:

```
cd goexpert-auction-api
```

### 3. Run Docker Compose

To run the project using Docker, use Docker Compose to build and start the containers:

```
docker compose up -d --build
```

This will build the Docker images and start the application containers.

### 4. Test the API

After the container is running, you can test the API using the following `curl` commands:

- To create a new **auction**:

```
curl -X POST http://localhost:8080/auction \
     -H "Content-Type: application/json" \
     -d '{
       "product_name": "Samsung Smart TV 65 QLED 4K",
       "category": "Home Electronics",
       "description": "QLED display with over 1 billion colors, 120Hz refresh rate and SmartThings compatibility."
       "condition": 0
     }'
```
Expected response: A `204 No Content` status code, with no response body, indicating the request was successfully processed without errors.

- To list **auctions** with a completed status:

- Note that you must wait for the time defined in the environment variable for auctions to be automatically marked as completed.

```
curl http://localhost:8080/auction?status=1
```

Expected response: A `JSON` object containing the data of the created auction(s).
