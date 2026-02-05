### Today I’ll walk you through our Knowledge Management Approach, specifically:
- How we are leveraging the **KM APIs**
- How it powers **RAG** experiences
- How a **Knowledge Base** is created
- How we organize **Knowledge Sources** and make that information accessible and usable within our documents and application chat experiences.

We added this deck to clarify our **Knowledge Management** approach because, through our discussions with SMEs and various teams, we realized there is still some confusions and assumptions about how the overall process works. 

To help everyone gain a clear, non‑technical understanding, we’ve included this overview.

Additionally, we have built a simple, scalable framework that can be applied across all products eliminating the need to create separate chatbots for each one. The framework supports a plug‑and‑play approach, and it can be easily cloned and configured within a day to address similar usecases efficiently. We've already implemented this for Onboarding Training AI and TechComm.

# Page 1 and Page 2
### The core elements of the KM (Knowledge Management) are Documents, KS (Knowledge Source), and KB (Knowledge Base).

1. **Documents** are the contents we ingest into a Knowledge Source. Contents such as User Guide, Report Guide, Training Guide, Reference File, etc for any of the Product provided in the formats like PDF, Docx, PPT, Text, or HTML file.
2. **Knowledge Source (KS)** is the origin or logical grouping of the ingested documents. You can think of it like a repository, folder, or library. For example, if the Product is BPS, all documents related to BPS are stored together under one Knowledge Source.
3. **Knowledge Base (KB)** is the structured environment that stores all **Knowledge Sources**. It indexes and organizes them to make the entire collection searchable and easy to retrieve.

# Page 3
To access a specific **Knowledge Base**, we use its **KBID (Knowledge Base ID)**. The **AI Enablement Team** provides a unique **KBID** along with a secure ID + key upon request. This ensures that each application instance connects to the correct **Knowledge Base** with proper security.

# Page 4 
### Why the KBID Is Important?
- **Document Ingestion:** When documents are ingested or re-ingested, the **KBID** makes sure they get placed in the correct **Knowledge Source**, so everything stays organized and separate from other **Knowledge Base**.
- **Chat RAG:** When someone asks a question, the **KBID** helps the system search only within the right environment, so the LLM can give an accurate and relevant answer.

# Page 5
### Each time we ingest content, 
- A unique **Document ID** is assigned to every file. This helps with chunk‑level troubleshooting, re‑ingesting specific documents.
- In addition, every **Knowledge Source** is assigned with a unique **KSID**. This lets us track ingestion status, and filtering at the source level. In our setup, this mapping aligns with Product‑level or Sub‑Product‑level.

# Page 6
- Documents are ingested and converted into **Vector Embeddings**. During this process, each document is chunked, embedded, and indexed as vectors in the **Vector Database** to enable fast semantic retrieval.
- When a user submits a query, the system retrieves the most relevant vectors, and the LLM uses that context to generate an accurate, meaningful response.
