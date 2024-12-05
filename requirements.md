# User needs:
- Application that supports users to pay the bill with multiple methods
- By keeping the paying history, allow users to track the payment
- Map function for saving where the expense has been paid
- Also the location of the members

# Target Audience:
- Users that has a group of friends that hang out often
- Or between family member
- Users supposed to be willing to share their location with the people in the friends list
- Of course they can turn off location or turn off from a specific person

# Feature list:
![image](https://github.com/user-attachments/assets/3a7fe7bb-8a12-4443-936d-6b1b564158dc)

## Login/Signup
## Guided tour to tell user how to use the app
## Adding friends:
  + A friend can chat and share location 
  + A friend don't have to be in a group
  + A friend can be unfriend anytime
  + A friend can added to a group anytime
## Navigation will let users interact between multiple features
## Friends tab for total balance friends owe you or vise versa
## groups tab for managing the group balance:
  + Users can upload or attach a proof such as bill, banktrans screenshot,... to the action they have made to create transparancy
## Activity with analytic tools support for user to keep track of the balance:
  + Activity log
  + Notifications for new expenses, settlements, or reminders about outstanding balances.
- Expense-adding button will be added in the middle of the navbar
  + Entry: expense detail, amount, desc, payer(friends/new friends by ID/ groups)
  + Specify who is the payer and how the bill are going to split to other group members
  + Expense can be divided equally or customized based on rules or percentage
## Settings: 
  + Profile manangement: noti, info, preference or linked payment methods
  + Currency options
## Settling balances:
  + Purpose: Update balances when members resolve debts by making payments to one another.
  + Examples: Logging a cash payment or a bank transfer made by one group member to another to settle an owed amount.
## Map function to enhance the UX:
![image](https://github.com/user-attachments/assets/4e8c607a-5664-42f3-9d86-4dd1d556ff68)

  + Users can click on the action tab to see the detail of that payment, a map view may be in the detail activity
  + User can also keep track of their friends location, clicking the map will show their friends marker as a avatar:
    + Users can search for the username in their friends list
    + turning off the location will show the latest updated location
    + Unless unfriend won't display the location anymore
    + Additional feature can be implemented with the api such as:
        + Direction to specific user
        + The map can also included history payment(marker in a restaurant)
