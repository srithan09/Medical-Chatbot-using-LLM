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

# (1).Document Loading
## Medical Book 
The **Gale Encyclopedia of Medicine (GEM)** and **Essentials of Medical Microbiology (EMM)** complement each other in providing comprehensive medical information. Together, these books cover thousands of diseases, disorders, and medical conditions, each following a structured, systemized approach to make information accessible for learners and professionals alike.

### Combined Features for Building a Chatbot:
1. **Broad Disease Coverage**: GEM provides detailed descriptions of medical conditions, while EMM focuses on microbiological aspects of diseases. Together, they can form a vast knowledge base, catering to a variety of queries.

2. **Structured Approach**: Both books use standardized formats, such as overviews, symptoms, diagnosis, and treatment, enabling consistent and reliable chatbot responses.

3. **Accessibility**: Content is written in a clear, concise manner, suitable for general users and healthcare professionals, which aligns with user-friendly chatbot interactions.

4. **Visual Aids**: Inclusion of diagrams, tables, and charts in both books enhances the user's understanding and can be leveraged for multimedia responses in the chatbot.

5. **Expert-Reviewed Content**: High-quality, evidence-based information ensures the chatbot's credibility and trustworthiness.
# (2). Splitting
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


