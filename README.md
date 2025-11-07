📊 #Automation Workflow: Date Difference & Trimester Calculation

This workflow reads a list of dates from a spreadsheet, calculates the number of days between each date and today, and determines which trimester of the year each date belongs to. The results are written into new columns within the same dataset.

#✅ What This Workflow Does

Reads a spreadsheet containing a column of dates.

Converts each value into a valid date format (supports Excel serial numbers).

Calculates the difference in days between the date and today.

Determines the trimester (Q1, Q2, Q3, or Q4) based on the month of the date.

Writes both results into new columns in the same row.

#🏗️ Workflow Logic
Step	Description
1	Read the input Excel/CSV file
2	Parse date column into proper date objects
3	Calculate day difference (today - date)
4	Detect trimester based on month
5	Output updated dataset
#🧮 Trimester Rules
Month Range	Trimester
January – March	Q1
April – June	Q2
July – September	Q3
October – December	Q4
#🧾 Example (Before → After)
Original Date	Difference (Days)	Trimester
2024-01-15	297	Q1
2024-05-02	190	Q2
2024-08-11	89	Q3
2024-11-23	10	Q4
#🧩 Core Logic Example (JavaScript for n8n)
const rows = $input.all();
const today = new Date();

function parseDate(value) {
  if (!value) return null;

  // If Excel serial date
  if (typeof value === 'number') {
    return new Date((value - 25569) * 86400 * 1000);
  }

  return new Date(value);
}

function getTrimester(date) {
  const month = date.getMonth() + 1;
  if (month >= 1 && month <= 3) return "Q1";
  if (month >= 4 && month <= 6) return "Q2";
  if (month >= 7 && month <= 9) return "Q3";
  return "Q4";
}

return rows.map(item => {
  const dateValue = parseDate(item.json.date);
  
  const difference = dateValue 
    ? Math.floor((today - dateValue) / (1000 * 60 * 60 * 24)) 
    : null;

  const trimester = dateValue ? getTrimester(dateValue) : null;

  return {
    json: {
      ...item.json,
      difference_in_days: difference,
      trimester: trimester
    }
  };
});

#🛠️ Tools Used

n8n for workflow automation

Excel / CSV for input/output data

JavaScript for processing logic

#🎯 Use Cases

HR contract aging reports

Subscription / billing cycle tracking

Maintenance scheduling

Academic / administrative reporting

Sales and performance dashboards
