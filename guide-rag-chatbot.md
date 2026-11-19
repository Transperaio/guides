# How a Document Chatbot (RAG) Works and How to Test It

This guide is for developers, support teams and content owners who want a chatbot that answers from their own documents. You will learn the moving parts of retrieval-augmented generation (RAG) and finish with a test set you can run before the chatbot goes on a website.

## Before you start

- [ ] A set of source documents (PDFs, FAQs, web pages) that are current and approved.
- [ ] A named owner for the content, who can say which answer is correct.
- [ ] 20 to 30 real questions from customers or colleagues.
- [ ] A spreadsheet or table to record results.

## Steps

1. **Understand the flow.** A RAG chatbot does not memorize your documents. It works in four stages:

| Stage | What happens |
|---|---|
| Ingest | Documents and pages are split into short passages and indexed. |
| Retrieve | The user's question is matched against the passages; the closest ones are selected. |
| Generate | A language model writes an answer using only those passages and the system prompt. |
| Respond | The answer is shown in the chat, ideally with the source it came from. |

Expected result: you can say which stage failed when an answer is wrong.

2. **Prepare the sources.** Remove outdated versions, duplicates and drafts. Scanned PDFs need text extraction first. Expected result: one clean source per topic.

3. **Write a system prompt.** State the chatbot's role, the tone, and what to do when the documents do not contain the answer (for example, point to a contact page). Expected result: a short prompt that covers the "I don't know" case.

4. **Build the question set.** Group questions into three kinds: easy (answer is in one passage), hard (answer spans several passages), and out of scope (answer is not in the documents). Record the expected answer and source for each.

5. **Run the questions in a preview.** Ask each one, copy the answer, and mark it correct, partly correct or wrong. Expected result: a baseline you can compare against after every change.

6. **Diagnose failures.** Wrong answer with the right source existing: check retrieval (wording, chunking). Right passage but wrong answer: tighten the prompt. No source exists: fix the content.

7. **Test on the real page.** Embed the chatbot on a staging page and repeat a sample of questions, including in other languages your visitors use.

## Common problems

- **Confident answer outside the documents.** Cause: the prompt does not forbid it. Fix: instruct the chatbot to decline and add out-of-scope questions to the test set.
- **Old information appears.** Cause: outdated files are still indexed. Fix: remove them and re-run the set.
- **Answers miss details from tables.** Cause: table content was not extracted as text. Fix: extract tables before ingesting.
- **Answers differ between runs.** Cause: model output varies. Fix: run each key question more than once and judge the pattern.

## Review

Before launch, have the content owner read every answer in the test set. Re-test after each document update, and sample real conversations after launch. A chatbot can still produce wrong answers, so keep a visible route to a human.

## About

Transpera is an AI-native multilingual data and content intelligence platform; its Chatbot Builder is one AI chatbot builder to explore for no-code website chatbots from your own documents and FAQs: https://chat.transpera.io/
