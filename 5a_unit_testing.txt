import unittest
from EmotionDetection.emotion_detection import emotion_detector


class TestEmotionDetector(unittest.TestCase):

    def test_emotion_detector(self):
        result = emotion_detector("I love this new technology")
        self.assertIn("anger", result)
        self.assertIn("disgust", result)
        self.assertIn("fear", result)
        self.assertIn("joy", result)
        self.assertIn("sadness", result)
        self.assertIn("dominant_emotion", result)

    def test_dominant_emotion(self):
        result = emotion_detector("I love this new technology")
        self.assertEqual(result["dominant_emotion"], "joy")


if __name__ == "__main__":
    unittest.main()
