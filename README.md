# automation-for-job-notification
Go to https://script.google.com.

Create a new project.

Paste the full code above.

Click the floppy disk icon 💾 to save. Name the project (e.g., “Daily Job Alert”).

In the top dropdown, select sendDailyDevOpsJobs.

Click the ▶️ Run button to trigger it manually.

Approve permissions the first time (click “Review Permissions” → Choose your account → Click “Advanced” → Continue → Allow).

code

function sendDailyDevOpsJobs() {
  var email = "hanamantkaroli39@gmail.com";
  var subject = "Daily DevOps Engineer Jobs (Last 24 Hours)";
  
  var searchQueries = [
    "DevOps Engineer site:linkedin.com/jobs",
    "DevOps Engineer site:indeed.com/jobs",
    "DevOps Engineer site:glassdoor.com/Job",
    "DevOps Engineer site:monsterindia.com",
    "DevOps Engineer site:naukri.com"
  ];
  
  var baseUrl = "https://www.google.com/search?q=";
  var timeFilter = "&tbs=qdr:d";  // qdr:d means results from last 24 hours
  
  var body = "Here are the latest DevOps job listings posted in the last 24 hours:\n\n";

  searchQueries.forEach(function(query) {
    var url = baseUrl + encodeURIComponent(query) + timeFilter;
    body += query + ":\n" + url + "\n\n";
  });
  
  MailApp.sendEmail(email, subject, body);
}
