----------------  Project Title: MCQ answer key generator -----------------------


-   answer_table.sql — creates the tables (student, answer_table, op_table) and loads sample student answers
-   answers.awk — reads a raw answer-key text file and prints INSERT INTO answer_table statements
-   answer_key_sample.txt — example input file, in the format the awk script expects


-----  How to run -----------

rm -f answers.db

sqlite3 answers.db < answer_table.sql

awk -f answers.awk answer_key_sample.txt > insert.sql

sqlite3 answers.db < insert.sql


---------check the results----------------------



sqlite3 -header -column answers.db "SELECT * FROM answer_table;"
