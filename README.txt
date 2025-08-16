SQL Lab Activity 2 – Stored Procedures and Cursors

Files in Submission

-   q1.sql → ListAllSubscribers()
-   q2.sql → GetWatchHistoryBySubscriber(IN sub_id INT)
-   q3.sql → AddSubscriberIfNotExists(IN subName VARCHAR(100))
-   q4.sql → SendWatchTimeReport()
-   q5.sql → SubscriberWatchHistories()
-   readme.txt 


Steps to Execute

1.  Open MySQL Workbench and connect to your database server.

2.  Create and use the database:

        CREATE DATABASE activity;
        USE activity;

3.  Create the required tables:

        CREATE TABLE Shows (
            ShowID INT PRIMARY KEY,
            Title VARCHAR(100),
            Genre VARCHAR(50),
            ReleaseYear INT
        );

        CREATE TABLE Subscribers (
            SubscriberID INT PRIMARY KEY,
            SubscriberName VARCHAR(100),
            SubscriptionDate DATE
        );

        CREATE TABLE WatchHistory (
            HistoryID INT PRIMARY KEY,
            ShowID INT,
            SubscriberID INT,
            WatchTime INT,
            FOREIGN KEY (ShowID) REFERENCES Shows(ShowID),
            FOREIGN KEY (SubscriberID) REFERENCES Subscribers(SubscriberID)
        );

4.  Insert sample data:

        INSERT INTO Shows (ShowID, Title, Genre, ReleaseYear) VALUES
        (1, 'Stranger Things', 'Sci-Fi', 2016),
        (2, 'The Crown', 'Drama', 2016),
        (3, 'The Witcher', 'Fantasy', 2019);

        INSERT INTO Subscribers (SubscriberID, SubscriberName, SubscriptionDate) VALUES
        (1, 'Emily Clark', '2023-01-10'),
        (2, 'Chris Adams', '2023-02-15'),
        (3, 'Jordan Smith', '2023-03-05');

        INSERT INTO WatchHistory (HistoryID, SubscriberID, ShowID, WatchTime) VALUES
        (1, 1, 1, 100),
        (2, 1, 2, 10),
        (3, 2, 1, 20),
        (4, 2, 2, 40),
        (5, 2, 3, 10),
        (6, 3, 2, 10),
        (7, 3, 1, 10);

5.  Execute each procedure file in order (q1.sql → q5.sql) by opening
    and running them in MySQL Workbench.

6.  Test the procedures with CALL statements, for example:

        CALL ListAllSubscribers();
        CALL GetWatchHistoryBySubscriber(2);
        CALL AddSubscriberIfNotExists('Alice Johnson');
        CALL SendWatchTimeReport();
        CALL SubscriberWatchHistories();

Git Repository

GitHub Repo Link: https://github.com/narsing64/ssd-lab-activity

Notes

-   Make sure delimiters (DELIMITER $$ ... $$) are correctly applied
    when creating procedures.
-   Run CALL procedure_name(); only after creating the procedures
    successfully.
