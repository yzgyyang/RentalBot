# RentalBot
A Rental Management Bot made for UWPC.

## To-do
- users database design + pending selection w/ json
- rentals database design
- renting process finish
- equips database design

## Server Addresses
Chatbot Webhook: https://uwpcrentalbot.herokuapp.com/  

## Deployment
The following secret values should be set in environmental variables instead of in the code:  
`FB_VERIFY_TOKEN`
`FB_ACCESS_TOKEN`

If you are deploying this app using Heroku (like I did), use Heroku CLI to set:
```
heroku config:set FB_VERIFY_TOKEN=your_verify_token
heroku config:set FB_ACCESS_TOKEN=your_access_token
```

## FB Messenger Platform Settings

To set a 'Get Started' button, use:
```bash
curl -X POST -H "Content-Type: application/json" -d '{
  "setting_type":"call_to_actions",
  "thread_state":"new_thread",
  "call_to_actions":[
    {
      "payload":"hey"
    }
  ]
}' "https://graph.facebook.com/v2.6/me/thread_settings?access_token=PAGE_ACCESS_TOKEN"
```

To set a 'Persistent Menu' for the bot, use:
```bash
curl -X POST -H "Content-Type: application/json" -d '{
  "persistent_menu":[
    {
      "locale":"default",
      "composer_input_disabled":false,
      "call_to_actions":[
        {
          "title":"Menu",
          "type":"nested",
          "call_to_actions":[
            {
              "title":"Our Inventory",
              "type":"postback",
              "payload":"inventory_category"
            },
            {
              "title":"Rental Requests",
              "type":"postback",
              "payload":"rental_requests"
            },
            {
              "title":"Exec Portal",
              "type":"postback",
              "payload":"auth_exec"
            }
          ]
        }
      ]
    }
  ]
}' "https://graph.facebook.com/v2.6/me/messenger_profile?access_token=YOUR_ACCESS_TOKEN_HERE"
```
