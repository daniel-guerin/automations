# Projects

## 1. CPD Outreach

### Problem

- **Current conversion rate**: Only 2 out of 50 people (4%) who receive a booking link actually book a CPD
- People receive booking links via email but fail to complete the booking process
- Two failure points: not clicking the link, or clicking but not finalizing a date

### Proposed Solutions

#### Email Segmentation & Follow-up

- Track link clicks and send **two different follow-up sequences**:
  - For those who **didn't click**: Re-engagement emails with different angles
  - For those who **clicked but didn't book**: Address decision paralysis
- **Suggest specific dates** instead of leaving selection open-ended (reduces indecision)

#### Engagement Sequence

- Implement a **10-step email sequence** leading up to booking
- Treat as a cold email nurture campaign
- Include benefits, case studies, and social proof
- Drip content over time to maintain engagement

#### Additional Tactics

- Add referral option: "Know a colleague who might be interested?"
- Explore additional value-adds to increase conversion (discuss with client)

#### Technical Stack

- **Integration**: Salesforce + Mailchimp + n8n

#### Tracing who booked

- Calendly

---

## 2. Awards Competition Automation

### Objective

Automate discovery of projects eligible for awards that use galvanized steel in **UK & Ireland**

### Data Sources

#### Magazine Subscriptions

- **RIBA Journal** (online subscription)
- **Architecture Today** (free)
- **Architects Journal** (online subscription)
- **New Steel Construction** (free)
- **Architects Review** (subscription)
- **Dezeen** (free)

#### Additional Sources

- Social media platforms (LinkedIn, Twitter, Instagram)
- Architecture/construction news sites

### Implementation Plan

1. **Automated web scraping** of listed magazines for relevant projects
2. **Social media monitoring** for galvanized steel projects
3. **Filter & qualify** projects that mention or likely use galvanized steel
4. **Automated outreach campaign** to project stakeholders
5. Follow-up nurture sequence for interested parties

### Challenges

- Not all sources explicitly mention "galvanized steel"
- Initial automation will require manual review/filtering
- Building confidence in automated classification over time

---

## 3. Cold Outreach for Project Database

### Overview

- Client has an existing database of project contacts
- Goal: Drive engagement through multiple touchpoints

### Conversion Paths

- Website visits
- Datasheet requests
- CPD booking requests
- Direct inquiries

### Target

- **10% conversion rate within one year**

### Strategy

- Design multi-touch cold email campaigns
- Personalized outreach based on project type/industry
- Clear CTAs for each conversion path
- Track and optimize based on engagement metrics

---

## 4. Extra CRM Seat (Inquiry Routing)

### Workflow

1. **Inquiry received** → Tagged with appropriate category in Salesforce
2. **Categorization**:
   - Technical inquiry → Inbox 1
   - General inquiry → Inbox 2
   - Awards inquiry → Inbox 3
   - (Additional categories as needed)
3. **Reply drafted** in Salesforce
4. **Reply sent** via n8n from appropriate inbox (not info@)

### Technical Implementation

- Set up **email aliases** for different inquiry types
- User selects alias in Salesforce → n8n routes through correct mailbox
- Maintains professional segmentation and tracking

---

## 5. Blog Creation Automation

### Focus Industries

- Water
- Power
- Solar
- Housing

### Current State

- Writer uses LLM models to assist
- **Current output**: 3-4 blogs per writer
- **Current cost**: £60 per 800-word blog
- Team member is developing landing pages for each industry

### Automation Opportunities

- **News observer agent**: Pull relevant industry news, facts & figures, project information
- Automated research compilation
- Draft generation with human review/editing
- Potentially increase output while reducing cost per blog

---

## 6. Datasheet and Publications Automation

### Problem

- **Emails going to spam**: MailChimp emails with multiple download links are flagged as spam
- Users request datasheets/publications from website but don't receive them
- Poor user experience impacts lead quality and engagement

### Current State

**Flow:**

1. User requests datasheets/publications from website
2. MailChimp automation triggered
3. MailChimp sends email with multiple download links
4. **Email lands in spam** ❌

### Proposed Solution

**Migrate from MailChimp to Make.com + Centralized Storage**

**New Flow:**

```
Website Form → Make.com Webhook → Update Salesforce → Retrieve OneDrive Links → Send HTML Email
```

**Step-by-Step:**

1. User submits request on website → Webhook to Make.com
2. **Make.com Scenario 1: Request Handler**
   - Parse JSON payload (which datasheets/publications requested)
   - Search Salesforce for Lead/Contact by email
   - Create or update record
   - Add Activity: "Requested Datasheet: [name]" or "Requested Publication: [name]"
   - Retrieve download links from OneDrive
   - Trigger Scenario 2
3. **Make.com Scenario 2: HTML Email Sender** (Already exists)
   - Triggered by Salesforce flow
   - Generate well-formatted HTML email
   - Insert OneDrive download links
   - Send via proper email infrastructure

### Technical Implementation

**Storage:**

- **OneDrive**: Centralized repository for all datasheets and publications
- Connected to Salesforce account
- Single source of truth for all downloadable assets
- Easy to manage/update files

**Make.com Integration:**

- **Scenario 1**: New - Request handler and SF updater
- **Scenario 2**: Existing - HTML email sender (already built and in use)
- Reuse existing infrastructure where possible

**Salesforce Tracking:**

- Every request logged as Activity on Lead/Contact
- Visibility into what content each lead is interested in
- Better lead scoring and qualification

---

## 7. Member Dashboard (Airtable)

### Objective

Create a modern, centralized dashboard for members to view key organization data and metrics in real-time.

### Data Sources & Content

#### Manual Entry Data

- **Standards** - Text table, manually updated
- **Environment** - Text table, manually updated
- **Steel Data** - Numerical data from external source, manual entry

#### Salesforce Data (Automated)

- **Enquiries** - Live data from Salesforce
- **CPD Sessions** - Live data from Salesforce
- **Inspections** - Internal data (could create Salesforce object for automation)

#### External Platform Data

- **Digital Comms - Website** - Google Analytics data
- **Digital Comms - Social** - Sprout Social reports (manual input or API integration)

### Requirements

#### Design

- **Modern, up-to-date format** - Clean, professional interface
- Responsive design for desktop and mobile viewing
- Clear data visualization (charts, graphs, tables)

#### Access Control

- **Backend access**: Admin team can input/update manual data
- **Frontend access**: Members can view via shareable link
- Read-only for members, edit access for admin team

#### Technical Stack Options

**Option 1: Airtable + Interface**

- **Pros**: Quick setup, no coding needed, built-in forms for data entry, native integrations
- **Cons**: Limited customization, ongoing subscription cost

**Option 2: Custom Dashboard (Retool/Softr + Airtable backend)**

- **Pros**: More customization, better member experience, branded design
- **Cons**: More setup time, technical expertise needed

**Option 3: Power BI + Salesforce + Google Sheets**

- **Pros**: Deep analytics, direct Salesforce integration, familiar to enterprise users
- **Cons**: Microsoft ecosystem dependency, steeper learning curve

### Proposed Data Flow

```
Data Sources → Airtable Base → Public Interface → Member View Link
```

**Data Sources:**

1. **Manual Input**: Admin team enters Standards, Environment, Steel Data via Airtable forms
2. **Salesforce**: Automated sync via Make.com or Zapier
   - Enquiries count/status
   - CPD bookings/attendance
   - Inspections data (if Salesforce object created)
3. **Google Analytics**: Export to Google Sheets → Import to Airtable (scheduled)
4. **Sprout Social**: Manual CSV upload or API integration if available

**Airtable Setup:**

- Create base with tables for each data category
- Set up relationships between tables
- Create Interface for member-facing view
- Generate shareable link with read-only access

### Implementation Considerations

**Data Update Frequency:**

- Manual data: As needed (Standards, Environment)
- Salesforce data: Daily sync recommended
- Google Analytics: Weekly or monthly
- Social media: Monthly

**Member Access:**

- Generate unique link or embed on members-only website section
- No login required (public but unlisted link)
- OR: Password-protected interface for additional security
