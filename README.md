<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Chubby Tea</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      padding: 20px;
      max-width: 700px;
      background-color: #016936;
      color: #FFD700;
      font-weight: bold;
    }
    button {
      padding: 10px 20px;
      margin: 10px 5px;
      background-color: black;
      color: white;
      font-weight: bold;
      border: none;
      cursor: pointer;
      border-radius: 5px;
    }
    button:hover {
      background-color: #333;
    }
    .output {
      margin: 15px 0;
      padding: 10px;
      border: 1px solid #444;
      border-radius: 5px;
      background-color: #222;
      color: #FFD700;
    }
    a {
      text-decoration: none;
      padding: 10px 20px;
      margin: 10px 5px;
      background-color: black;
      color: white;
      font-weight: bold;
      border-radius: 5px;
      display: inline-block;
    }
    a:hover {
      background-color: #333;
    }
  </style>
</head>
<body>

  <h1>Chubby Tea</h1>
  <p>Click the button below to generate a review. Use the link to leave a review on Yelp!</p>

  <button onclick="generateReview()">Generate a Review</button>
  <button onclick="copyToClipboard()">Copy to Clipboard</button>
  <div id="reviewOutput" class="output">Your review will appear here.</div>

  <a href="https://www.yelp.com/writeareview/biz/38eXlFZ8UD_ExersL2-Smg?review_origin=review-feed-war-widget" target="_blank">Leave a Yelp Review</a>

  <script>
    // Components for dynamic review generation
    const openers = [
      "Danny C suggested I try Chubby Tea, and I am so glad I did!",
      "Thanks to Danny C, I discovered Chubby Tea.",
      "Danny C recommended Chubby Tea, and it was worth every sip.",
      "I followed Danny C’s advice to visit Chubby Tea.",
      "Danny C’s suggestion to check out Chubby Tea was spot on.",
    ];

    const descriptivePhrases = [
      "the staff was incredibly polite and accommodating",
      "the service was prompt and professional",
      "the atmosphere was vibrant and welcoming",
      "the drinks were bursting with flavor",
      "the menu offered a great variety",
      "the flavors were unique and refreshing",
    ];

    const specificDetails = [
      "the mango coconut slushy was a perfect treat on a hot day",
      "the herbal hot tea was soothing and aromatic",
      "the milk tea was rich and perfectly brewed",
      "the taro topping added an amazing texture to my drink",
      "the green bean topping was a surprising delight",
      "the grapefruit kumquat green tea was zesty and refreshing",
    ];

    const closers = [
      "I’ll definitely return!",
      "Looking forward to trying more from the menu.",
      "This spot has become my new favorite.",
      "Highly recommended for tea lovers!",
    ];

    // Array to track unique reviews
    let generatedReviews = [];

    function generateReview() {
      let review;

      // Keep generating until a unique review is created
      do {
        const opener = openers[Math.floor(Math.random() * openers.length)];
        const descriptive = descriptivePhrases[Math.floor(Math.random() * descriptivePhrases.length)];
        const detail = specificDetails[Math.floor(Math.random() * specificDetails.length)];
        const closer = closers[Math.floor(Math.random() * closers.length)];

        review = `${opener} I found that ${descriptive}. In particular, ${detail}. ${closer}`;
      } while (generatedReviews.includes(review));

      // Add the unique review to the tracking array
      generatedReviews.push(review);

      // Display the review
      const reviewOutput = document.getElementById("reviewOutput");
      if (reviewOutput) {
        reviewOutput.textContent = review;
      } else {
        console.error("Output element not found!");
      }
    }

    function copyToClipboard() {
      const reviewText = document.getElementById("reviewOutput")?.textContent;
      if (reviewText && reviewText !== "Your review will appear here.") {
        navigator.clipboard.writeText(reviewText).then(() => {
          alert("Review copied to clipboard!");
        }).catch(err => {
          console.error("Failed to copy:", err);
        });
      } else {
        alert("No review to copy! Generate a review first.");
      }
    }
  </script>

</body>
</html>
