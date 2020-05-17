---
layout: post
title:  "Use reCAPTCHA v3 with Flask"
date:  20200517 23:56:35 +0800
categories: default
tags:
 - reCAPTCHA
 - Flask
---

## Frontend

a simple HTML form with `grecaptcha`: 

 - the script will call `grecaptcha` to fetch a reponse,  
 - the respone will be sent together with the form so that backend can verify the `grecaptcha` response.


```
<html>
<head>
    <script src="https://www.google.com/recaptcha/api.js?render={reCAPTCHA_site_key}"></script>

    <script>
        grecaptcha.ready(function () {
            grecaptcha.execute('{reCAPTCHA_site_key}', {action: 'validate_captcha'}).then(function (token) {
                console.info("got token: " + token);
                document.getElementById('g-recaptcha-response').value = token;
            });
        });
    </script>
</head>

<body>
<form>
    <input name="email" type="email">

    <input type="hidden" id="g-recaptcha-response" name="g-recaptcha-response">
    <input type="hidden" name="action" value="validate_captcha">
    <input type="submit" class="btn btn-primary" value="Generate RSS"/>
</form>

<html>

```


## Backend

a simple http call to veify the `grecaptcha` response sent by frontend:


```
@app.route('/handle', methods=["POST"])
def lists():
    parameters = request.form

    recaptcha_passed = False
    recaptcha_response = parameters.get('g-recaptcha-response')
    try:
        recaptcha_secret = os.environ.get('RECAPTCHA_SECRET')
        response = requests.post(f'https://www.google.com/recaptcha/api/siteverify?secret={recaptcha_secret}&response={recaptcha_response}').json()
        recaptcha_passed = response.get('success')
    except Exception as e:
        print(f"failed to get reCaptcha: {e}")
```