# Dwelling - Personalized Apartment Search Platform

Dwelling is a data-driven apartment recommendation system that enhances traditional rental search by incorporating **neighborhood context, sentiment, and lifestyle fit**—not just price and unit features. By combining unstructured data (Reddit text, apartment images) with structured location and apartment data, Dwelling provides more holistic and personalized housing recommendations .

**Team Members**
Joseph Bailey · Jack Feen · Peyton Gibbs · Humphrey Hui · **Archie Korale** · Sam LeFebre

---

## The Problem

**What renters actually care about**

* Neighborhood safety
* Places to eat
* Schools nearby
* Activities and lifestyle fit

**What rental websites typically provide**

* Apartment features
* Price
* Location

Dwelling bridges this gap by pulling data from **hundreds of nearby locations, social discussions, and apartment images** to deliver recommendations that better reflect real renter priorities .

---

## Questions

* How can unstructured data improve apartment recommendations?
* Can neighborhood sentiment be quantified and meaningfully integrated into housing search?
* How do proximity and lifestyle preferences impact perceived apartment quality?
* Can we personalize recommendations for different renter profiles (e.g., young professionals vs. families)?

---

## Methodology

### Data Sources

* **Apartment Information**: Name, address, rent, beds, baths
* **Images**: Apartment photos
* **Reddit Posts & Comments**: Neighborhood-specific discussions
* **Nearby Locations**: Schools, grocery stores, nightlife, healthcare
* **Neighborhood Grouping**: 14 custom Austin neighborhood clusters based on zip code

### Data Collection

* **Selenium**: Scraped apartment metadata
* **APIs**: Pulled nearby locations and Reddit data
* **Google Cloud Vision API**: Processed 150 apartment images in ~78 seconds

### Feature Engineering

* **Computer Vision**

  * Generated binary amenity indicators (e.g., pool, balcony, modern kitchen)
  * Calculated luxury scores based on premium materials and design features
* **NLP & Sentiment Analysis**

  * VADER sentiment scoring for Reddit posts (range: −1 to 1)
  * roBERTa + keyword matching to assign posts to neighborhoods
* **Scoring Framework**

  * Apartment Feature Score: **10%**
  * Neighborhood Sentiment Score: **30%**
  * Local Features & Proximity Score: **60%**
  * Distance scoring based on normalized distance to user-defined target locations
  * Cosine similarity used to match user text preferences with apartment features .

---

## Results

Dwelling successfully generated **personalized apartment recommendations** based on different renter personas:

### Test Case 1: Young Adult

* Priorities: college proximity, thrift shops, nightlife
* Result: *The Capitol Living* (1108 Nueces St)
* Highlights:

  * 6 minutes to UT Austin
  * 2 minutes to Downtown / 6th Street

### Test Case 2: Young Family

* Priorities: elementary schools, pediatrician, grocery store
* Result: *River Stone Ranch* (5701 S Mopac Expy)
* Highlights:

  * Between two elementary schools
  * 5–10 minutes from medical center and Target

These tests demonstrated Dwelling’s ability to adapt recommendations to **distinct lifestyle needs**, validating the effectiveness of integrating unstructured data into housing search .

---

## Future Work

* Expand to additional cities
* Incorporate real-time pricing and availability
* Add interactive UI for preference weighting
* Improve sentiment classification with fine-tuned domain models

