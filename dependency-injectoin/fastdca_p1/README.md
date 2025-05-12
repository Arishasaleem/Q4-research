📘 Dependency Injection in FastAPI
❓ What is Dependency Injection?
Dependency Injection (DI) ek design pattern hai jisme aap ek function ya class ko uski zarurat ki cheezein (dependencies) automatically provide karte ho — bina manually create kiye.

"Injection" ka matlab hai: kisi function ya class ke andar cheezon ko automatically daalna.

🚀 Why use Dependency Injection?
✅ Code reuse karne ke liye

✅ Cleaner and modular code

✅ Testing easy hoti hai

✅ Complex logic (like auth, DB) ko manage karne ke liye

🔧 How Dependency Injection works in FastAPI?
FastAPI Depends() function ka use karta hai to inject dependencies automatically.

python
Copy
Edit
from fastapi import FastAPI, Depends

app = FastAPI()

# This is a dependency function
def get_simple_goal():
    return {"goal": "We are building AI Agents Workforce"}

# This is a route using dependency injection
@app.get("/get-simple-goal")
def simple_goal(response: dict = Depends(get_simple_goal)):
    return response
👉 Breakdown:
get_simple_goal() ek reusable function hai — ye dependency hai.

Depends(get_simple_goal) FastAPI ko bolta hai:

"Is route ke liye get_simple_goal() run karo aur uska result response mein daal do."

FastAPI automatically function call karta hai — aapko manually call karne ki zarurat nahi.

✅ Real-life Example – Authentication
python
Copy
Edit
def get_current_user(token: str = Depends(oauth2_scheme)):
    # Token verify karke user ka data return karo
    return {"username": "john_doe"}

@app.get("/profile")
def get_profile(user: dict = Depends(get_current_user)):
    return {"message": f"Welcome {user['username']}"}
Yahan:

get_current_user ek dependency hai

FastAPI user ka token verify karke user variable mein result daal deta hai

🧠 Key Points to Remember:
Use Depends() jab:

Aapko logic reuse karna ho

Aapko FastAPI se automatic handling chahiye

Dependency function kuch bhi ho sakta hai: simple return, DB query, auth check, etc.

Yeh testing aur maintenance ko easy banata hai.

📦 Extra Tip: Use with Classes
python
Copy
Edit
class Settings:
    def __init__(self):
        self.db_url = "sqlite://"

def get_settings():
    return Settings()

@app.get("/config")
def config(settings: Settings = Depends(get_settings)):
    return {"db_url": settings.db_url}
