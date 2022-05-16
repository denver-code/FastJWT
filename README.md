# FastJWT
FastJWT is a micro library for hide some work process while generating JWT

# How to use
1. Download file ```fast_jwt.py``` and put into work directory.  
2. Import from your auth file class named FastJWT from downloaded file.
3. In first step you need initialize class and set your secret_key:
```python
from fast_jwt import FastJWT

FastJWT().set_secret_key("SUPERSECRETKEY")
```
4. For generate JWT use some like this:
```python
jwt_token = await FastJWT().encode(
    optional_data={
        "This is": "Optional like user info"
        }
    )
```
5. Also you can decode your token(for example in "login_required):
```python
jwt_token = await FastJWT().decode(
    Authorization
    )
```
6. And you use depend like basic login_required for
 create secured page, he can see if token already in
 Headers and check signature and check expire(token life) time. Can put into dependencies like this:
```python
@app.get("/secure", dependencies=[
    Depends(
        FastJWT().login_required
        )
    ])
async def secure_page():
    return {
        "message": "Welcome on secure page!"
        }
```

# Example usage
```bash
$ git clone https://github.com/denver-code/FastJWT
$ cd FastJWT
$ python3 -m venv .venv
$ source .venv/bin/activate
$ pip3 install -r requirements.txt
$ uvicorn example:app --reload
```