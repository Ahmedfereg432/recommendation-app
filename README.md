# Recommendation App

A Python-based e-commerce recommendation engine using Flask. This app provides both content-based and collaborative filtering recommendations for products, and exposes a simple API for integration.

## Features

- **Hybrid Recommendation System**: Combines collaborative filtering (SVD) and content-based filtering (TF-IDF + price) for improved results.
- **RESTful API**: Easily get recommendations via HTTP endpoints.
- **Scalable Design**: Built with pandas, scikit-learn, and Surprise for flexibility.
- **CORS Enabled**: Allows integration with frontends hosted elsewhere.

## How It Works

- **Content-Based Filtering**: Uses product names, brands, categories, and price to find similar items.
- **Collaborative Filtering**: Uses user-product interactions and a trained SVD model to recommend products based on user preferences.
- **Hybrid Approach**: Dynamically combines both strategies using user interaction history.

## API Endpoints

### `/`
Returns API documentation in JSON.

### `/hybrid`
Hybrid recommendations (collaborative + content-based).

**Parameters:**
- `user_id` (required): User ID string.
- `product_id` (optional): Seed product ID for content-based bias.
- `top_n` (optional, default: 30): Number of recommendations to return.

**Example:**
```
/hybrid?user_id=68476733e0b3981f8a711165&top_n=5
```

### `/content`
Content-based recommendations for a given product.

**Parameters:**
- `product_id` (required): Seed product ID.
- `top_n` (optional, default: 30): Number of recommendations.

**Example:**
```
/content?product_id=683dc98cc029c78e3af4fb0d
```

## Setup & Usage

### Prerequisites

- Python 3.7+
- `pip install -r requirements.txt`
- Required files:  
  - `GRAD.products.csv`: Product data  
  - `user_interactions.csv`: (optional, for collaborative filtering)  
  - `svd_model.h5`: Pre-trained SVD model (optional, for collaborative filtering)

### Running the App

```bash
python app.py
```
The API will be available at `http://localhost:5000/`.

### Example Request

```bash
curl "http://localhost:5000/hybrid?user_id=12345&top_n=5"
```

## Project Structure

```
recommendation-app/
├── app.py
├── GRAD.products.csv
├── user_interactions.csv
├── svd_model.h5
├── requirements.txt
└── README.md
```

## Extending

- Update `GRAD.products.csv` with new products.
- Re-train and update the SVD model with new interaction data for better collaborative recommendations.
- Expand API with new endpoints as needed.

## License

MIT License

---

**Author:** [Ahmedfereg432](https://github.com/Ahmedfereg432)