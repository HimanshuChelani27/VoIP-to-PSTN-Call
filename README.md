# Twilio Flask Voice Calling App

This is a **Flask** web application that enables **in-browser voice calls** using **Twilio**. It provides an API to generate **Twilio access tokens** and handle **voice call requests**.

## 🚀 Features

- ✔️ Generates **Twilio access tokens** for authentication
- ✔️ Supports **outgoing and incoming voice calls** via Twilio
- ✔️ Uses **Flask** to handle API requests
- ✔️ Configurable via **environment variables**

## 📌 Prerequisites

Before running the application, ensure you have the following:

* ✅ **Python 3** installed
* ✅ A **Twilio account** (Sign up [here](https://www.twilio.com/try-twilio))
* ✅ A Twilio:
   * **Account SID**
   * **API Key SID**
   * **API Key Secret**
   * **TwiML App SID**
   * **Twilio Phone Number**
* ✅ `pip` for package management

## 📥 Installation

1️⃣ Clone this repository:

```sh
git clone https://github.com/HimanshuChelani27/VoIP-to-PSTN-Call.git
cd VoIP-to-PSTN-Call
```

2️⃣ Create a **virtual environment** (optional but recommended):

```sh
python -m venv venv
source venv/bin/activate # On macOS/Linux
venv\Scripts\activate # On Windows
```

3️⃣ Install dependencies:

```sh
pip install -r requirements.txt
```

4️⃣ Set up **environment variables**:
Create a `.env` file in the project root and add the following:

```ini
TWILIO_ACCOUNT_SID=your_account_sid
TWILIO_API_KEY_SID=your_api_key_sid
TWILIO_API_KEY_SECRET=your_api_key_secret
TWIML_APP_SID=your_twiml_app_sid
TWILIO_NUMBER=your_twilio_phone_number
```

**Replace** `your_*` placeholders with your **Twilio credentials**.

## ▶️ Running the Application

Start the **Flask server**:

```sh
python app.py
```

The application will be available at: ➡️ `http://localhost:3000/`

## 📡 API Endpoints

### `GET /`
➡️ **Renders the homepage.**

### `GET /token`
➡️ **Generates and returns a Twilio access token.**

**Response:**
```json
{
    "token": "your_generated_token",
    "identity": "your_twilio_phone_number"
}
```

### `POST /handle_calls`
➡️ **Handles incoming and outgoing Twilio calls.**

**Request Parameters:**
* `To` (optional) – The recipient's phone number for outbound calls.

**Response:**
* ✅ If `To` is specified and **not** the Twilio number, it **initiates an outbound call**.
* ❌ If `To` is **missing** or matches the Twilio number, it **does nothing**.

## 🚀 Deployment

To deploy this app, you can use services like **Heroku**, **AWS**, or **DigitalOcean**.

1️⃣ Make sure `gunicorn` is installed:

```sh
pip install gunicorn
```

2️⃣ Run the app using Gunicorn:

```sh
gunicorn -w 4 -b 0.0.0.0:3000 app:app
```

## 📜 License

This project is **open-source** and available under the **MIT License**.
