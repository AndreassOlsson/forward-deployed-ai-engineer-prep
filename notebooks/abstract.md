# Abstract: The Forward Deployed AI Engineer

The FDAIE does not jump the gun and starts coding as soon as the customer has stopped talking. The FDAIE is more like a detective and business advisor who ALSO has strong coding and AI capabilities.

## How A FDAIE Reacts To A Problem

When a customer reaches out because the production deployment is showing unexpected failures our first reaction should be to make sure we truly understand the problem.

### We ask the customer to clarify the failure before making any conclusions

We ask for the customer to clarify, to the best of their capabilities:

- Who is responsible for the system?
- What percentage of operations are failing?
- Are failures random or consistent?
- Did they start after a certain deployment?
- Are all customers affected or only some?
- What error messages are visible?
- Is the core system, the data transformation logic, or the destination CRM (Customer Relationship Management) failing?

### We should try to recreate the issue

We then try to reproduce the issue. For integrated systems it may often be good to check:

- Request payload
- Response body
- HTTP Status codes
- Logs
- Request ID
- CRM API Repsonse
- Field Mapping (data schema validation)
- Authentication state
- Rate-limit headers

#### Know that demo data is usually different from production data

Its important to know that demo data is usually clean (happy path) and that production data is messy (unhappy path). We should compare the demo and production data in terms of:

- Required fields
- Null values
- Invalid formats
- Unexpected enum values
- Large payloads
- Duplicate records
- Permission differences
- API rate limits
- Authentication behaviour

#### Know how to separate the root cause

The issues may come from:

- Data quality problems
- CRM validation rules
- API rate limits
- Authentication expiry
- Incorrect production credentials
- Missing field mappings
- Environment configuration mismatch
- Retry logic failure
- Timeout issues

### We create a short-term fix

Depending on urgency:

- Add better validation
- Skip invalid records with clear error reporting
- Add retry with backoff
- Reduce sync batch size
- Fix mapping for known failing fields
- Add a dead-letter queue for failred records
- Provide customer-facing status visibility

### We communicate clearly to the customer and dont hide uncertainty

We might say to the customer

"The demo worked because the data was clean. In production, several records were failing because requried CRM fields were missing or formatted differently. I am separating valid records from invalid ones, adding clearer error reporting and creating a retry-safe path so the sync can continue while we fix the bad records."

### We then prevent future reoccurences

After the immediate fix:

- Add data validation before sync
- Add monitoring and alerts
- Add sync success/failure dashboard
- Add structured error categories
- Add retry and dead-letter handling
- Add test cases using real produciton-like data
- Document CRM field requirements

## How a FDAIE thinks

1. Customer problem
2. Clarify business impact
3. Understand current workflow
4. Inspect data and system constraints
5. Identify failure mode
6. Design practical fix
7. Communicate trade-offs
8. Deploy safely
9. Monitor and improve
