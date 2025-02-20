# Music-Store-Data-Analytics

Overview
This project focuses on analyzing an online music store database using SQL. By working with real-world data, you will gain hands-on experience in data querying, relationship management, and business analytics. This project is beginner-friendly and aims to help users understand how SQL can be used to extract insights from a structured dataset.

Objectives
Analyze customer transactions and purchasing behavior.
Explore music sales trends to identify popular genres, artists, and albums.
Understand relationships between customers, invoices, and tracks.
Optimize SQL queries for efficient data retrieval and reporting.
Database Schema
The music store database consists of multiple interrelated tables, including:

Artist – Stores artist names.
Album – Stores album details linked to artists.
Track – Contains music tracks, including genre, media type, and pricing.
Genre – Defines music categories.
Customer – Stores customer information, including location and contact details.
Invoice – Records purchases made by customers.
InvoiceLine – Contains details of purchased tracks in each invoice.
Employee – Stores employee details, including managers.
Playlist – Represents customer-generated music playlists.
Tools & Technologies
PostgreSQL / MySQL for database management.
PgAdmin4 for executing queries and database visualization.
SQL Queries for data analysis, joins, and aggregation.
SQL Queries Used
This project includes SQL queries to:

Retrieve the top-selling genres and artists.
Identify customer purchase trends.
Generate sales reports based on invoice details.
Analyze employee performance in handling customer accounts.
Extract customer demographics for marketing insights.
Getting Started
Step 1: Clone the Repository
bash
Copy
Edit
git clone https://github.com/yourusername/SQL_Project_Music_Store_Analysis.git  
cd SQL_Project_Music_Store_Analysis
Step 2: Import the Database
Open PgAdmin4 or any SQL client.
Import the provided Music Store Database file.
Verify the table relationships and schema.
Step 3: Run SQL Queries
Open queries.sql in your SQL client.
Run individual queries to explore different aspects of the database.
Example Queries
1️⃣ Get the Top 5 Best-Selling Genres
sql
Copy
Edit
SELECT g.Name AS Genre, SUM(il.Quantity) AS Total_Sales  
FROM InvoiceLine il  
JOIN Track t ON il.TrackId = t.TrackId  
JOIN Genre g ON t.GenreId = g.GenreId  
GROUP BY g.Name  
ORDER BY Total_Sales DESC  
LIMIT 5;
2️⃣ Retrieve Customer Purchase History
sql
Copy
Edit
SELECT c.FirstName, c.LastName, COUNT(i.InvoiceId) AS Purchase_Count, SUM(i.Total) AS Total_Spent  
FROM Customer c  
JOIN Invoice i ON c.CustomerId = i.CustomerId  
GROUP BY c.FirstName, c.LastName  
ORDER BY Total_Spent DESC;
3️⃣ Find the Most Popular Artists
sql
Copy
Edit
SELECT ar.Name AS Artist, COUNT(il.InvoiceLineId) AS Total_Tracks_Sold  
FROM InvoiceLine il  
JOIN Track t ON il.TrackId = t.TrackId  
JOIN Album al ON t.AlbumId = al.AlbumId  
JOIN Artist ar ON al.ArtistId = ar.ArtistId  
GROUP BY ar.Name  
ORDER BY Total_Tracks_S
