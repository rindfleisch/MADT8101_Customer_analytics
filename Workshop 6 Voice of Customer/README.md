# Klook's Voice of Customers

![Logo_rgb](https://github.com/rindfleisch/MADT8101_Customer_analytics/assets/82042221/bad4d24f-1976-438d-9831-ee74f10d3151)

## Objective
Topic modeling(LDA) and Document clustering for Klook's Universal Studios Japan Studio Pass customer reviews

### Difference between Topic modeling(LDA) and Document clustering
topic modeling with LDA is about discovering hidden topics within documents, while document clustering is about grouping documents based on their overall content similarity.

## Data
![package](https://github.com/rindfleisch/MADT8101_Customer_analytics/assets/82042221/8e4ad35a-c700-4d6d-aec2-f4226d16263c)

[The reviews](https://www.klook.com/th/activity/46604-universal-studios-japan-e-ticket-osaka-qr-code-direct-entry/?spm=Home.Popular%3Aany%3A%3APopularActivities%3ACard_LIST&clickId=1b43082dd5) of the above package have been used for the analytics

## Topic modeling with LDA
Applying LDA topic modeling to Klook reviews enhances understanding of customer sentiment and preferences, enabling personalized recommendations and service improvements. Below is Intertopic Distance Map and Top-30 Most Relevant Terms for Topic 1, 2 and 3 visualization

![v1](https://github.com/rindfleisch/MADT8101_Customer_analytics/assets/82042221/33f2a05c-a24c-4a42-9d5b-6e244f28dda6)

![v2](https://github.com/rindfleisch/MADT8101_Customer_analytics/assets/82042221/6b5b306c-1df5-400f-96bb-704c39e0e30d)

![v3](https://github.com/rindfleisch/MADT8101_Customer_analytics/assets/82042221/465cff2a-bebe-4bfc-89b2-dd4a2d269675)

The majority of the comments revolve around the ticket, highlighting its convenience and value proposition

## Document Clustering
Model universal-sentence-encoder-multilingual/3 has been used and embeded the comments into arrays

### K-means
Before proceeding, methods for finding optimal k was processed which are Elbow and Silhouette 

![k-means](https://github.com/rindfleisch/MADT8101_Customer_analytics/assets/82042221/3db2b0b0-a228-4135-8962-a0334a348716)

![silhoe](https://github.com/rindfleisch/MADT8101_Customer_analytics/assets/82042221/2add5c2b-6fe7-4731-a27e-48dd1843e93f)

Both methods are in complete alignment, firmly indicating that the most suitable value for k is 2.

```
Cluster ID : 0

Most common words include : [('บัตร', 4), ('จอง', 3), ('สะดวก', 3), ('ไม่ต้อง', 3), ('ตั๋ว', 3), ('มือถือ', 2), ('สั่งซื้อ', 1), ('universalstudiosjapanosaka', 1), ('จองตั๋ว', 1), ('UniverseStudiosJapaninOsaka', 1)]

Cluster ID : 1

Most common words include : [('ใช้งาน', 4), ('สะดวก', 4), ('USJ', 3), ('คุ้มค่า', 2), ('เหมาะสำหรับ', 2), ('คน', 2), ('พก', 2), ('อ', 2), ('คิว', 2), ('หน้า', 2)]

```

### Cosine Similarity

```
Cluster ID : 0

Most common words include :[('ซื้อ', 14), ('บัตร', 12), ('จอง', 11), ('คน', 9), ('ตั๋ว', 9), ("','", 8), ('เล่น', 6), ('เครื่องเล่น', 6), ('ไม่ต้อง', 6), ('สะดวก', 6)]

Cluster ID : 1

Most common words include :[('สะดวก', 5), ('มือถือ', 3), ('ไม่ต้อง', 3), ('ตั๋ว', 3), ('คิว', 2), ('ซื้อ', 2), ("','", 2), ("['", 1), ('ก้อ', 1), ('เสียเวลา', 1)]
```

From both method, it can be seen quite clear that K-means is better in this case since the most common words can be separated in to 2 groups.

First group is about booking ticket conveniently while the second cluster is about worth spending and utilizing.

However, both of the clusters still shares a common word which is convenience that it can be misinterpreted. 
