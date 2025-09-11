# Backend‑Extract‑PDF‑AI

Backend‑Extract‑PDF‑AI is a TypeScript/Express API + Web monorepo for extracting, viewing, editing, saving, listing, updating, and deleting PDF documents with AI assistance.

---

## Deployed Links (Vercel)

* **Web frontend**: [https://backend-extract-pdf-ai-web.vercel.app](https://backend-extract-pdf-ai-web.vercel.app)
  *(Replace with your actual web URL)*

* **API backend**: [https://backend-extract-pdf-ai.vercel.app](https://backend-extract-pdf-ai.vercel.app)
  *(Replace with your actual API URL)*

---

## Demo


---

## Setup & Environment

### Requirements

* Node.js (version ≥ 16 recommended)
* npm or yarn
* A MongoDB database
* (Optional) AI provider API key (Gemini or GROQ or other, depending on your AI implementation)

### Environment Variables

Create a `.env` file in the root of your **api** (backend) project (or where specified) with at least the following:

```dotenv
MONGODB_URI=your_mongodb_connection_string
GEMINI_API_KEY=your_gemini_key        # or
GROQ_API_KEY=your_groq_key
# plus any other env vars your code expects, e.g.
PORT=3000
AI_MODEL_NAME=whatever-if-used
```

---

## How to Run Locally

From the repo root, assuming a structure like:

```
/apps
  /api    ← backend
```

You can run each part separately:

```bash
# Install all dependencies
npm install
```

Then in separate terminals:

```bash
# Backend (API)
cd apps/api
npm run dev
```

* The backend will typically run on something like `http://localhost:3000`
---

## API Documentation

Here are the main API routes, with sample requests & responses.

| Method   | Route                              | Description                                       | Sample Request                                                                                                            | Sample Response                                                                                                            |
| -------- | ---------------------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `GET`    | `/api/pdf/invoices?search=<query>` | List or search invoices                           | `GET https://{YOUR_API_URL}/api/pdf/invoices?search=a`                                                                    | `200 OK` <br> `json { "invoices": [ { "id": "123", "filename": "invoice1.pdf", "text": "...extracted text..." }, ... ] } ` |
| `POST`   | `/api/pdf/invoices/upload`         | Upload a new PDF for processing                   | `POST https://{YOUR_API_URL}/api/pdf/invoices/upload` <br> Content-Type: `multipart/form-data` with file field            | `201 Created` <br> `json { "id": "123", "filename": "invoice1.pdf", "status": "processing" } `                             |
| `GET`    | `/api/pdf/invoices/:id`            | Get details of a specific invoice                 | `GET https://{YOUR_API_URL}/api/pdf/invoices/123`                                                                         | `200 OK` <br> `json { "id": "123", "filename": "invoice1.pdf", "text": "...extracted text..." } `                          |
| `PUT`    | `/api/pdf/invoices/:id`            | Update metadata or edited fields of a PDF invoice | `PUT https://{YOUR_API_URL}/api/pdf/invoices/123` <br> Payload: `{ "filename": "newname.pdf", "text": "edited text..." }` | `200 OK` <br> `json { "id": "123", "filename": "newname.pdf", "text": "edited text..." } `                                 |
| `DELETE` | `/api/pdf/invoices/:id`            | Delete an invoice                                 | `DELETE https://{YOUR_API_URL}/api/pdf/invoices/123`                                                                      | `204 No Content`                                                                                                           |

> Note: Adjust the routes if your codebase differs.

---

## Additional Notes

* Ensure CORS is properly configured in the backend (especially if the frontend is hosted on a different domain).

---

## License

*(Optional: Add your license here, e.g., MIT License)*

---

Thank you — contributions & issues welcome!
