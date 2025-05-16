# ARTIFICIAL-INTELLIGENCE-
from sumy.parsers.plaintext import PlaintextParser
from sumy.nlp.tokenizers import Tokenizer
from sumy.summarizers.lsa import LsaSummarizer

def summarize_text(text, sentence_count=2):
    parser = PlaintextParser.from_string(text, Tokenizer("english"))
    summarizer = LsaSummarizer()
    summary = summarizer(parser.document, sentence_count)
    return ' '.join(str(sentence) for sentence in summary)

def main():
    print("Enter text (type 'END' on a new line to finish input):")
    lines = []
    while True:
        line = input()
        if line.strip().upper() == 'END':
            break
        lines.append(line)
    
    full_text = '\n'.join(lines)
    print("\nOriginal Text:\n" + full_text)
    
    summary = summarize_text(full_text)
    print("\nSummary:\n" + summary)

if __name__ == "__main__":
    main()
