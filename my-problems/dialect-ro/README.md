**Statement link:** [DialectRO - Difficulty: EASY | MLCompete | MLCompete](https://platform.olimpiada-ai.ro/en/problems/218)

1. **Why did I add this?**
   
   _Note: Solving this problem does not require the use of Transformer-type architectures (e.g., RoBERTa)._
   
   The thing is that if you copy-paste the problem statement (without that note, of course) into an LLM (I tested Claude, Gemini, and ChatGPT), they will tell you to use transformers (which makes sense, since this should be a difficult task). However, I adapted the dataset so that you can use a more classic approach (TF-IDF on chars). That’s why the problem is labeled as "Easy".

2. **Why does TF-IDF work so well?**:
   TF-IDF works because this specific dataset is a **vocabulary-matching game**, not a language-understanding task.

   The "Standard," "Moldavian," and "Banat" labels are distinguished by **exact character sequences** (regionalisms and archaic spellings) rather than complex sentence structures.

   ### The Mechanics:
   1.  **Standard Language "Nuking":** 90% of the words in all three classes are identical (standard Romanian). TF-IDF's **IDF** component mathematically zeros these out, effectively deleting the "Standard" noise and leaving only the regional markers.

   2.  **Feature Orthogonality:** Unlike modern AI, TF-IDF treats *pâni* and *pâini* as **completely different dimensions**. It doesn't care that they mean the same thing; it only cares that *pâni* appears in Moldavian texts and *pâini* appears in Standard ones. This makes the classes **linearly separable**.
   
   3.  **Suffix Detection:** By using **Character N-grams**, TF-IDF captures regional phonetic endings (like those in the Banat dialect) without needing to understand grammar. It just flags the specific string sequences as high-weight anchors.

   In short: It works because the "correct" answer is hidden in **spelling variations**, and TF-IDF is the most efficient tool for weighting those variations while ignoring the shared vocabulary.

3. **How to achieve an F1 score of 1?**
   
   Use transformers.

   (Check `perfect-solution.ipynb`)

