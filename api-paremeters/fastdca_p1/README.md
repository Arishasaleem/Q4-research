# 🚀 FastAPI Item Update API

This is a simple FastAPI project demonstrating how to use **path**, **query**, and **body** parameters with validation using `Path`, `Query`, and `Body` from FastAPI.

---


## 📦 Features


- `PUT` endpoint to update item data
- 
- Parameter validation using FastAPI tools
- 
- Request body model defined using Pydantic
- 
- Supports optional query strings and JSON body
- 

---

## 🛠️ Installation

Make sure you have **Python 3.10+** installed.

1. **Clone the repo**
2. 
   ```bash
   
   git clone https://github.com/yourusername/fastapi-item-api.git
   
   cd fastapi-item-api
   
Create and activate virtual environment (optional)

bash
Copy
Edit
python -m venv env
source env/bin/activate  # On Windows: env\Scripts\activate
Install dependencies

bash
Copy
Edit
pip install fastapi uvicorn
🚀 Run the App
bash
Copy
Edit
uvicorn main:app --reload
Visit http://127.0.0.1:8000/docs to explore the interactive Swagger UI.

🔄 API Endpoint
PUT /items/validated/{item_id}
Update an item using path, query, and body parameters.

📥 Parameters
Location	Name	Type	Required	Description
Path	item_id	int	✅ Yes	ID of the item (must be ≥ 1)
Query	q	str	❌ No	Optional search query (min length: 3)
Body	item	Item	❌ No	Optional JSON object with item details

📦 Item Model (Body)
json
Copy
Edit
{
  "name": "Sample Item",
  "description": "Optional description",
  "price": 19.99
}
Field	Type	Required	Description
name	string	✅ Yes	Name of the item
description	string	❌ No	Item description
price	float	✅ Yes	Price of the item

🧪 Example Request
http
Copy
Edit
PUT /items/validated/5?q=book
Content-Type: application/json

{
  "name": "Book Title",
  "description": "A nice read",
  "price": 10.5
}
✅ Example Response
json
Copy
Edit
{
  "item_id": 5,
  "q": "book",
  "item": {
    "name": "Book Title",
    "description": "A nice read",
    "price": 10.5
  }
}
📚 Built With
FastAPI

Pydantic

Uvicorn

📝 License
This project is licensed under the MIT License.

🙋‍♂️ Author
Made with ❤️ by Arisha saleem
Feel free to contribute or fork!

