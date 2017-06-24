# StackOverFlow LogIn

Sample app to LogIn to StackOverFlow

Here is an example for Entering text in search box and Click search button in Bing

 1. Use [WebView][1] to do all the work

        WebView webView = new WebView();
 2. Use [`InvokeScriptAsync`][2] method for WebView to **use JS code**

        webView.InvokeScriptAsync("eval", new string[] {});
 3. **Get the HTML** of the site using below code

        private async void GetHTMLAsync()
        {
            var siteHtML = await webView.InvokeScriptAsync("eval", new string[] { "document.documentElement.outerHTML;" });
        }
 4. **Enter text** in search box using below code

        private async void EnterTextAsync(string enterText)
        {
            var functionString = string.Format(@"document.getElementsByClassName('b_searchbox')[0].innerText = '{0}';", enterText);
            await webView.InvokeScriptAsync("eval", new string[] { functionString });
        }
 5. **Simulate click** using below code

        private async void SimulateClickAsync()
        {
            var functionString = string.Format(@"ddocument.getElementsByClassName('b_searchboxSubmit')[0].click();");
            await webView.InvokeScriptAsync("eval", new string[] { functionString });
        }
 6. Get new site's HTML using **Step 3**

  [1]: https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.WebView
  [2]: https://msdn.microsoft.com/en-us/library/windows/apps/dn301841.aspx?f=255&MSPPError=-2147217396
