<html>
<head>
  <link href="https://fonts.googleapis.com/css?family=Roboto" rel="stylesheet" type="text/css">
  <script src="https://apis.google.com/js/api:client.js"></script>
  <script>
  var googleUser = {};
  var startApp = function() {
    gapi.load('auth2', function(){
      // Retrieve the singleton for the GoogleAuth library and set up the client.
      auth2 = gapi.auth2.init({
        client_id: '712991549285-del0rc8c17cj3qhpqee77m0r83ipgvun.apps.googleusercontent.com',
        cookiepolicy: 'single_host_origin',
        // Request scopes in addition to 'profile' and 'email'
        //scope: 'additional_scope'
      });
      attachSignin(document.getElementById('customBtn'));
    });
  };

  function attachSignin(element) {
    console.log(element.id);
    auth2.attachClickHandler(element, {},
        function(googleUser) {
          document.getElementById('name').innerText = "Signed in: " +
              googleUser.getBasicProfile().getName();
        }, function(error) {
          alert(JSON.stringify(error, undefined, 2));
        });
  }
  </script>
  <style type="text/css">
    #customBtn {
      display: inline-block;
      background: white;
      color: #444;
      width: 190px;
      border-radius: 5px;
      border: thin solid #888;
      box-shadow: 1px 1px 1px grey;
      white-space: nowrap;
    }
    #customBtn:hover {
      cursor: pointer;
    }
    span.label {
      font-family: serif;
      font-weight: normal;
    }
    span.icon {
      background: url('/identity/sign-in/g-normal.png') transparent 5px 50% no-repeat;
      display: inline-block;
      vertical-align: middle;
      width: 42px;
      height: 42px;
    }
    span.buttonText {
      display: inline-block;
      vertical-align: middle;
      padding-left: 42px;
      padding-right: 42px;
      font-size: 14px;
      font-weight: bold;
      /* Use the Roboto font that is loaded in the <head> */
      font-family: 'Roboto', sans-serif;
    }
  </style>
  </head>
  <body>
  <!-- In the callback, you would hide the gSignInWrapper element on a
  successful sign in -->
  <div id="gSignInWrapper">
    <span class="label">Sign in with:</span>
    <div id="customBtn" class="customGPlusSignIn">
      <span class="icon"></span>
      <span class="buttonText">Google</span>
    </div>
  </div>
  <div id="name"></div>
  <script>startApp();</script>
  <h2>Welcome....</h2>  
  
@if (Request.IsAuthenticated)  
{   
    <a href='@Url.Action("LogOut", "Register")' onclick='navigate(this.href);'>  
        <input style="float: right;" type="button" value='Logout' />  
    </a>  
}  
@model UserRegistration.Models.UserLogin  
  
@{  
    ViewBag.Title = "Login";  
}  
  
<h2>Login</h2>
@using (Html.BeginForm())   
{  
    @Html.AntiForgeryToken()  
      
    <div class="form-horizontal">  
        <hr />  
        @Html.ValidationSummary(true, "", new { @class = "text-danger" })  
        <div class="form-group">  
            @Html.LabelFor(model => model.EmailId, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.EmailId, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.EmailId, "", new { @class = "text-danger" })  
            </div>  
        </div>  
  
        <div class="form-group">  
            @Html.LabelFor(model => model.Password, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.Password, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.Password, "", new { @class = "text-danger" })  
            </div>  
        </div>  
  
        <div class="form-group">  
            @Html.LabelFor(model => model.Rememberme, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                <div class="checkbox">  
                    @Html.EditorFor(model => model.Rememberme)  
                    @Html.ValidationMessageFor(model => model.Rememberme, "", new { @class = "text-danger" })  
                </div>  
            </div>  
        </div>  
  
        <div class="form-group">  
            <div class="col-md-offset-2 col-md-10">  
                <input type="submit" value="Create" class="btn btn-default" />  
            </div>  
        </div>  
    </div>  
}  
  
<div>  
    @Html.ActionLink("Back to List", "Index")  
</div>  
  
<script src="~/Scripts/jquery-1.10.2.min.js"></script>  
<script src="~/Scripts/jquery.validate.min.js"></script>  
<script src="~/Scripts/jquery.validate.unobtrusive.min.js"></script>  

    ViewBag.Title = "Index";  
}  
  
<h2>User Registration</h2>  
  
@using (Html.BeginForm())   
{  
    @Html.AntiForgeryToken()  
      
    <div class="form-horizontal">  
  
        <hr />  
        @Html.ValidationSummary(true, "", new { @class = "text-danger" })  
        <div class="form-group">  
            @Html.LabelFor(model => model.FirstName, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.FirstName, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.FirstName, "", new { @class = "text-danger" })  
            </div>  
        </div>  
  
        <div class="form-group">  
            @Html.LabelFor(model => model.LastName, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.LastName, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.LastName, "", new { @class = "text-danger" })  
            </div>  
        </div>  
  
        <div class="form-group">  
            @Html.LabelFor(model => model.Email, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.Email, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.Email, "", new { @class = "text-danger" })  
            </div>  
        </div>  
  
       <div class="form-group">  
            @Html.LabelFor(model => model.Password, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.Password, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.Password, "", new { @class = "text-danger" })  
            </div>  
        </div>  
  
        <div class="form-group">  
            @Html.LabelFor(model => model.ConfirmPassword, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.ConfirmPassword, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.ConfirmPassword, "", new { @class = "text-danger" })  
            </div>  
        </div>  
  
        <div class="form-group">  
            <div class="col-md-offset-2 col-md-10">  
                <input type="submit" value="Create" class="btn btn-default" />  
            </div>  
        </div>  
    </div>  
}  
<script src="~/Scripts/jquery-1.10.2.min.js"></script>  
<script src="~/Scripts/jquery.validate.min.js"></script>  
<script src="~/Scripts/jquery.validate.unobtrusive.min.js"></script> 
  
@model UserRegistration.Models.ChangePassword  
  
@{  
    ViewBag.Title = "ChangePassword";  
}  
  
<h2>ChangePassword</h2>
@model UserRegistration.Models.ForgetPassword  
  
@{  
    ViewBag.Title = "ForgetPassword";  
}  
  
<h2>ForgetPassword</h2>  
  
@using (Html.BeginForm())   
{  
    @Html.AntiForgeryToken()      
    <div class="form-horizontal">  
        <hr />  
        @Html.ValidationSummary(true, "", new { @class = "text-danger" })  
        <div class="form-group">  
            @Html.LabelFor(model => model.EmailId, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.EmailId, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.EmailId, "", new { @class = "text-danger" })  
@Html.ValidationMessage("EmailNotExists", new { @class = "text-danger" })  
            </div>  
        </div>  
  
        <div class="form-group">  
            <div class="col-md-offset-2 col-md-10">  
                <input type="submit" value="Create" class="btn btn-default" />  
            </div>  
        </div>  
    </div>  
}  
  
<div>  
    @Html.ActionLink("Back to List", "Index")  
</div>  
  
<script src="~/Scripts/jquery-1.10.2.min.js"></script>  
<script src="~/Scripts/jquery.validate.min.js"></script>  
<script src="~/Scripts/jquery.validate.unobtrusive.min.js"></script>  
@using (Html.BeginForm())   
{  
    @Html.AntiForgeryToken()  
      
    <div class="form-horizontal">  
        <h4>ChangePassword</h4>  
        <hr />  
        @Html.ValidationSummary(true, "", new { @class = "text-danger" })  
        <div class="form-group">  
            @Html.LabelFor(model => model.OTP, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.OTP, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.OTP, "", new { @class = "text-danger" })  
            </div>  
        </div>  
  
        <div class="form-group">  
            @Html.LabelFor(model => model.Password, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.Password, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.Password, "", new { @class = "text-danger" })  
            </div>  
        </div>  
  
        <div class="form-group">  
            @Html.LabelFor(model => model.ConfirmPassword, htmlAttributes: new { @class = "control-label col-md-2" })  
            <div class="col-md-10">  
                @Html.EditorFor(model => model.ConfirmPassword, new { htmlAttributes = new { @class = "form-control" } })  
                @Html.ValidationMessageFor(model => model.ConfirmPassword, "", new { @class = "text-danger" })  
            </div>  
        </div>  
  
        <div class="form-group">  
            <div class="col-md-offset-2 col-md-10">  
                <input type="submit" value="Change Password" class="btn btn-default" />  
            </div>  
        </div>  
    </div>  
}  
  
<div>  
    @Html.ActionLink("Login", "Login")  
</div>  
  
<script src="~/Scripts/jquery-1.10.2.min.js"></script>  
<script src="~/Scripts/jquery.validate.min.js"></script>  
<script src="~/Scripts/jquery.validate.unobtrusive.min.js"></script>
</body>
</html>
