# Lab Auth API

    INNER JOIN – Returns only rows where there is a match in both tables.
    LEFT JOIN – Returns all rows from the left table, plus matching rows from the right table (NULL if no match).
    RIGHT JOIN – Returns all rows from the right table, plus matching rows from the left table (NULL if no match).
    FULL OUTER JOIN – Returns rows when there is a match in either left or right table (some SQL dialects need UNION for this).
    CROSS JOIN – Returns the Cartesian product of both tables (every row from the left table combined with every row from the right table).
    SELF JOIN – A table joined with itself, usually with an alias, to compare rows in the same table.
    LEFT JOIN + Subquery – A pattern where you join a table with the result of another query.
    
## Endpoints List

| Endpoint                        | SQL Concept              | Purpose                                                                 |
|---------------------------------|--------------------------|-------------------------------------------------------------------------|
| **GET /reports/users-with-roles**   | INNER JOIN               | Shows users with their assigned roles.                                  |
| **GET /reports/users-with-profiles**| LEFT JOIN                | Shows users with their profile info (all users, even without profiles). |
| **GET /reports/roles-right-join**   | RIGHT JOIN               | Shows all roles, including roles not assigned to any user.              |
| **GET /reports/profiles-full-outer**| FULL OUTER JOIN / UNION  | Shows all users and profiles, whether or not they are linked.           |
| **GET /reports/user-role-combos**   | CROSS JOIN               | Lists all possible combinations of users and roles.                     |
| **GET /reports/referrals**          | SELF JOIN                | Shows users who referred other users.                                   |
| **GET /reports/latest-login**       | LEFT JOIN + Subquery     | Shows each user’s most recent login (or `Never` if no login exists).    |



