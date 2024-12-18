# Medical-chatbot-using-LLM
```bash
pip install -r requirements.txt
```
After installing the nesccesary requirements we need to create the folder structure for the project to be running and storing various components of files so we run the list_of_files which is been created in **template.py** 
``` bash
python template.py
```
# System Diagram
![System Diagram](research/Architecture%20Diagram/system_diagram_REU_drawio.png)

## Medical Book 
The **Gale Encyclopedia of Medicine (GEM)** is a comprehensive and authoritative reference source covering a wide range of medical topics, including diseases, disorders, treatments, drugs, diagnostic procedures, and medical advancements. Written by medical professionals and reviewed by experts, it serves as a reliable resource for accurate, up-to-date health and medical information.

**Features of the Gale Encyclopedia of Medicine:**

**1) Comprehensive Coverage:** GEM includes thousands of entries that provide detailed explanations of medical terms, conditions, and procedures.

**2) Clarity and Accessibility:** Content is written in a way that balances technical detail with accessibility, making it suitable for both medical professionals and the general public.

**3) Standardized Format:** Each entry follows a consistent format, typically including an overview, symptoms, causes, diagnosis, treatment options, and prognosis.

**4) Expert Review:** Entries are vetted by healthcare experts, ensuring high-quality, evidence-based information.

**5)Illustrations and Tables:** Many articles include diagrams, charts, and tables that enhance understanding.

## Extracting and Splitting Text from PDFs for Easy Processing
To extract text from a PDF and split it into manageable chunks for further processing, we use tools like PyPDFLoader and RecursiveCharacterTextSplitter. Here’s an explanation of how this is done step by step:

### Step 1: Loading the PDF
1) PyPDFLoader is a utility that facilitates reading and extracting text content from PDF files.
2) The loader reads the PDF document page by page, extracting the textual content while handling encoding issues that PDFs often have.
3) It essentially transforms the PDF’s raw text into a Python-friendly format, like strings or structured data.

### Step 2: Splitting Text into Chunks
After loading the text from the PDF, the extracted content is often a single block of text or split only by pages. This needs to be broken down further into smaller, more manageable chunks for processing, especially when dealing with NLP tasks or vector embeddings.

1. Recursive Splitting Logic:

- The splitter divides the text into chunks based on a predefined maximum character limit.
- It uses a hierarchical approach, first attempting to split on larger boundaries (e.g., paragraphs) and, if necessary, progressively splitting on smaller boundaries (e.g., sentences, words).

2. Preserving Context:

- By prioritizing splitting at logical boundaries (like paragraphs or sentences), it preserves the natural flow of the text. This ensures that the chunks remain coherent and contextually meaningful.

3. Configurable Parameters:

- Chunk Size: The maximum number of characters allowed in a single chunk.
- Chunk Overlap: To ensure context continuity between chunks, overlapping content (e.g., the last few sentences of one chunk appearing at the start of the next) can be configured.

4. Handling Edge Cases:

- For PDFs with special formatting or non-linear text flow (e.g., columns, tables), the splitter ensures that these structures are maintained as well as possible during splitting.

### Step 3: Resulting Text Chunks
The output of this process is a list of text chunks, where:

- Each chunk is coherent and respects logical boundaries.
- Chunk sizes are optimized for downstream processing, such as embedding generation or feeding into NLP models.
- Overlaps, if configured, ensure no loss of context between consecutive chunks.


