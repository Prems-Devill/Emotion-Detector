from flask import Flask, request, render_template
from EmotionDetection.emotion_detection import emotion_detector

app = Flask(__name__)


@app.route("/")
def home():
    return render_template("index.html")


@app.route("/emotionDetector")
def emotion_detector_route():
    text_to_analyze = request.args.get("textToAnalyze", "")

    if not text_to_analyze.strip():
        return "Please enter a text to analyze."

    result = emotion_detector(text_to_analyze)

    return str(result)


if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
