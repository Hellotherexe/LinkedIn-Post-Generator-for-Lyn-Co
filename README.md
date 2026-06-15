# Lyn&Co Realty LinkedIn AI Post Generator (n8n Workflow)

A fully automated n8n workflow that transforms screenshots of articles into high-quality LinkedIn posts, published directly to **LinkedIn Company Pages**.

---

## HOW IT WORKS

1. **UPLOAD** : User selects article screenshots via a custom web interface.
2. **OCR EXTRACT** : Images are processed via OCR.space to extract text.
3. **AI GENERATE** : Google Gemini creates tailored, data-driven LinkedIn posts.
4. **HOST IMAGE** : Images are uploaded to **Cloudinary** for public URL generation.
5. **REVIEW** : Users edit generated posts in a custom UI.
6. **PUBLISH** : Approved posts are sent via **Buffer** GraphQL to LinkedIn.

---

## SETUP INSTRUCTIONS

### 1. IMPORT
   Download the `linkedin-generator-workflow.json` and use the **Import from File** feature inside your n8n canvas.

### 2. CONFIGURE CREDENTIALS
   - **OCR Node** : Update `apikey` in the "OCR" node using your [OCR.space](https://ocr.space/) key.
   - **Gemini Node** : Add your Google Gemini API credential.
   - **Cloudinary** : Update the `1. Upload Image (Cloudinary)` HTTP node with your API key/Cloud name.
   - **Buffer Node** : 
     - **Authorization** : Use `Bearer YOUR_BUFFER_PERSONAL_API_KEY`.
     - **Channel ID** : Set `channelId` to your Company Page ID (from your Buffer dashboard URL).

### 3. WEBHOOK SYNC
   - Open **Respond to Webhook (UI)**.
   - Ensure the `fetch()` calls for `/webhook/batch-processor` and `/webhook/approve-linkedin` match your production URL.

### 4. AI PROMPT TUNING
   - Open the **AI Agent** node.
   - Update the "FORMAT RULES" and "TASK" sections to match your company's tone and brand guidelines.

---

## PREREQUISITES
   - **Buffer Account** : Ensure your Company Page is connected.
   - **Cloudinary** : Free tier is sufficient for temporary image hosting.
   - **n8n Instance** : Ensure your instance is reachable via a public URL for Webhooks.

---
