# Sales_insight
project 1 sales insight of cities
-- Answer the questions from the Sales team in this file.


-- Active Cities
select
city
from grp_member
where member_status ='active';
/*i clicked on grp_member and then i looked at status and they have 2 active and prereg. i dont know what prereg means maybe look into that.
the table has many cities that are active.*/

select
city,
state
from city
where city not in ( select distinct
city
from grp_member
where member_status = 'active');
/*from the previous table their was many cities that had active members but on this table it has 3 cities and these are not chicago, san franisco and new york. so maybe their is other major cities that have letsmeet */




-- Groups
select
join_mode,
count(join_mode)
from grp
group by join_mode;
/* their are open 3602, approval 723, closed 15. maybe something to look into is that how long does it take to get approved and why are some cloes*/ 





-- Categories
select
category_name,
count(group_id)
from grp
join category on grp.category_id = category.category_id
group by category_name
order by count(group_id) desc
limit 5;
/* tech 911, career& business 790, socializing 320, health 218, language 166. the top 2 have way more bigger number maybe we need to find out why and mabe focus more on the top 2*/

select
category_name,
count(group_id)
from grp
join category on grp.category_id = category.category_id
group by category_name
order by count(group_id) asc
limit 5;
/* Paranormal	4 Cars & Motorcycles	15,Sci-Fi & Fantasy	16, Lifestyle	26, Hobbies & Crafts	32. these are the least but we dont know how many people are in those groups.*/


-- Members
 select
 count(distinct( member_id))
 from grp_member;
 /* 39980 members we dont know if these people are in mutiple groups*/
 
 
 select
 (select
 count(distinct(member_id))
 from grp_member
 where city = 'chicago')
 /(select
 count(distinct(member_id))
 from grp_member);

/* 21.19% memeber are in chicago mabe something to look into people who live in the outskirts of the big city would they still be considered with the big city*/

 
 
