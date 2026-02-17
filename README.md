## Running Tests

### 1. Run tests locally

1. Create a virtual environment (optional but recommended):

python3 -m venv venv
source venv/bin/activate   # macOS/Linux
# venv\Scripts\activate    # Windows

2. Install dependencies:

python3 -m pip install --upgrade pip
python3 -m pip install -r requirements.txt

3. Run the tests:

python3 -m pytest -v

---

### 2. Run tests with Docker

1. Build the Docker image:

docker build -t python-client-tests .

2. Run tests in a container:

docker run --rm python-client-tests

- `--rm` cleans up the container after running
- Tests run automatically inside the container
