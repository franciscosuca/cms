# CMS Test Suite

This is the "Developer-First" path. By using **Payload 3.0**. This projects targets one deployment, one hosting bill ($0), and one repository.

## Phase 1: Local Setup

You will need [Node.js](https://nodejs.org/) installed. Use the official Payload template which comes pre-configured with React.

1. **Open your terminal** and run the following command to create the project:

    ```bash
    npx create-payload-app@latest my-test-site
    ```

2. **During the setup wizard, select these options:**
    - **Template:** `blank` (or `website` if you want a head start).
    - **Database:** `MongoDB` or `PostgreSQL`.
    - **Storage:** `Local Disk` (for this test).

3. **Navigate into your folder and start the engine:**

    ```bash
    cd my-test-site
    npm run dev
    ```

    _Your site is now running at `http://localhost:3000`. You can access the CMS at `/admin`._

## Phase 2: The Database

Vercel doesn't store your database, so you need a free cloud provider to hold your text and images.

1. **Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register).**
2. Create a **Shared Cluster** (the Free Tier).
3. Create a username and password
4. Under **Network Access**, allow access to your current IP
5. Copy your **Connection String** into the .env (it looks like `mongodb+srv://username:password@cluster...`).

## Phase 3: Initialize Payload

1. Run the project: npm run dev
2. Create first admin user (add screenshot)
3. Seed database (add screenshot)
4. Go to the website and click through the pages (add screenshot)

---

👨‍🔬 Under investigation ⬇️

---

## Phase 4: Defining Your Content (The "Products")

In your code editor (like VS Code), go to the `collections/` folder. Your developer will create a file called `Products.ts`:

```typescript
export const Products = {
  slug: "products",
  fields: [
    { name: "title", type: "text", required: true },
    { name: "description", type: "textarea" },
    { name: "image", type: "upload", relationTo: "media" },
  ],
};
```

_Once saved, your non-tech team will immediately see a "Products" menu in the admin panel where they can type and upload photos._

## Phase 5: Deployment to Vercel

1. **Push your code to GitHub.**
2. **Log into [Vercel](https://vercel.com/)** and click "Add New Project."
3. **Import your GitHub repository.**
4. **Environment Variables:** This is the most important step. You must add:
    - `MONGODB_URL`: (The connection string from Phase 2).
    - `PAYLOAD_SECRET`: (Any random long string of text).
5. **Click Deploy.** Vercel will give you a live URL (e.g., `my-test-site.vercel.app`).

## Phase 6: Analytics (The "Eyes")

1. **Go to [Google Analytics](https://analytics.google.com/).**
2. Create a "Property" for your website.
3. Find your **Measurement ID** (starts with `G-`).
4. **In your React code:** Install a small library to handle the tracking:

    ```bash
    npm install react-ga4
    ```

5. **Initialize it** in your main `layout.tsx` or `App.js` file:

    ```javascript
    import ReactGA from "react-ga4";
    ReactGA.initialize("G-XXXXXXXXXX");
    ```

## Summary of Actions for the Non-Tech Team

Once you hand this over, their "job" looks like this:

1. **Log in:** Go to `your-site.com/admin`.
2. **Add Content:** Click "Products" > "Add New."
3. **Publish:** Type the text, drag in a photo, and hit "Publish."
4. **View Results:** Open the Google Analytics app on their phone to see the visitor spikes.

## Next Steps

- Finish the excercise of running the project in the cloud
- Design website based on current design from client. Make a design based on Stich.
- ...
- (Based on the feedback about the design think about what solution will be better for then...)
- (1. Design project from 0 with CMS)
- (2. Design project as react only and then integrate CMS)
- ...
- Adapt the project to be able to run the components in locally
  - Documentation
  - Rely on docker-compose
