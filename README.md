// Categories for dynamic review generation
const openers = [
  "Danny C suggested I try Chubby Tea, and it was amazing!",
  "Thanks to Danny C, I discovered Chubby Tea.",
  "Danny C recommended Chubby Tea, and it was worth every sip.",
  "I followed Danny C’s advice to visit Chubby Tea.",
  "Danny C’s suggestion to check out Chubby Tea was spot on."
];

const descriptions = [
  "the staff was incredibly polite and accommodating",
  "the service was quick and efficient",
  "the atmosphere was vibrant and welcoming",
  "the drinks were perfectly balanced in flavor",
  "the menu offered a great variety of options",
  "the flavors were unique and refreshing"
];

const specifics = [
  "the mango coconut slushy was a perfect treat on a hot day",
  "the herbal hot tea was soothing and aromatic",
  "the milk tea was rich and perfectly brewed",
  "the taro topping added an amazing texture to my drink",
  "the green bean topping was a surprising delight",
  "the grapefruit kumquat green tea was zesty and refreshing"
];

const closers = [
  "I’ll definitely return!",
  "Looking forward to trying more from the menu.",
  "This spot has become my new favorite.",
  "Highly recommended for tea lovers!",
  "I can’t wait to bring my friends here."
];

// Set to track generated reviews
let generatedReviews = new Set();

/**
 * Generate a single unique review.
 */
function generateUniqueReview() {
  let review;

  // Ensure uniqueness
  do {
    const opener = openers[Math.floor(Math.random() * openers.length)];
    const description = descriptions[Math.floor(Math.random() * descriptions.length)];
    const specific = specifics[Math.floor(Math.random() * specifics.length)];
    const closer = closers[Math.floor(Math.random() * closers.length)];

    review = `${opener} I found that ${description}. In particular, ${specific}. ${closer}`;
  } while (generatedReviews.has(review));

  // Add to the set of generated reviews
  generatedReviews.add(review);

  return review;
}

/**
 * Generate a specified number of unique reviews.
 * @param {number} count - Number of unique reviews to generate.
 * @returns {string[]} Array of unique reviews.
 */
function generateReviews(count) {
  const reviews = [];

  // Check if it's possible to generate the requested number of unique reviews
  const maxCombinations = openers.length * descriptions.length * specifics.length * closers.length;
  if (count > maxCombinations) {
    throw new Error(`Cannot generate ${count} unique reviews. Maximum possible is ${maxCombinations}.`);
  }

  // Generate the reviews
  while (reviews.length < count) {
    reviews.push(generateUniqueReview());
  }

  return reviews;
}

// Example: Generate 5 unique reviews
const uniqueReviews = generateReviews(5);
console.log(uniqueReviews);
