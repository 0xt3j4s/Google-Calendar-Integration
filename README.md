# Google-Calendar-Integration

This project implements Google Calendar integration using Django REST API. The project utilizes OAuth2 authentication to obtain events from user's calendar after getting the access to user's calendar. 

## Getting Started
1. Clone the repository
```bash
git clone https://github.com/0xt3j4s/Google-Calendar-Integration-API.git
```
2. Move to the project directory
```bash
cd Google-Calendar-Integration-API
```
3. Move to the `google_calendar_integ` directory
```bash
cd google_calendar_integ
```

4. Configure the project settings, including the Google API credentials and changing the production secret in `settings.py`.

5. Run the server
```bash
python manage.py runserver
```

## API Endpoints
1. Initialize Google Calendar Integration
- Endpoint: `/rest/v1/calendar/init/`
- View: `GoogleCalendarInitView`

This endpoint starts step 1 of the OAuth2 process. It gets the user's credentials and saves the state so the callback can verify the auth server response.



2. Handle redirect from Google OAuth2 and get list of events from user's calendar
- Endpoint: `/rest/v1/calendar/redirect/`
- View: `GoogleCalendarRedirectView`

This endpoint handles redirect request sent by google, fetched the access token and then gets a list of 10 events from user's calendar. <br>
As of now, it only fetches the events from the 1st-31st May 2023. This can be changed by changing the `timeMin` and `timeMax` parameters in the `get_events` method of `GoogleCalendarRedirectView` class. 



## Implementation
- Used Django Framework to integrate Google Calendar. 
- It does not rely on any third-party libraries other than Google's provided standard libraries.


## Output
The events are rendered in a simple HTML page. The output is shown below: 
<br>

![Output](/output/events.jpeg)