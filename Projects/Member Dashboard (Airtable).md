# Member Dashboard Technical Research

**Project:** Member Dashboard (Airtable)
**Research Type:** Technical/Architecture Research
**Date:** 2025-10-28
**Researcher:** Winston (Architect)

---

## Executive Summary

This research evaluates the technical feasibility and implementation approach for migrating the client's member dashboard from its current platform (custom-built extranet) to Airtable. The research confirms **Airtable is fully capable** of replicating and enhancing all 8 current dashboard sections with native Interface Designer features, providing a modern, maintainable solution with superior access control and data integration capabilities.

**Key Findings:**

- Airtable Team plan (€20/month single seat) enables **password-protected sharing for unlimited members**
- Existing n8n subscription can handle all data sync requirements (**no additional cost**)
- MCP (Model Context Protocol) access available for programmatic base setup
- Airtable subscription cost: **€20/month** (€240/year)

---

## Current Dashboard Analysis

### System Overview

The existing member dashboard is a custom-built extranet featuring:

- **8 distinct dashboard sections** accessible via top navigation bar
- **Consistent design**: Navy/purple sidebar + light blue content area
- **Professional branding**: Organization logo + personalized greeting
- **Multi-source data integration**: Salesforce, Google Analytics, Sprout Social, manual entry

### The 8 Dashboard Sections

#### 1. **Enquiries Dashboard**

**Data Source:** Salesforce

**Visualizations:**

- Bar chart: Service line enquiries by category (579 total)
- Pie chart: Breakdown by enquirer type

**Categories Tracked:**

- Academic, Architect, Civil/Struct Engineer, Cons Engineer
- Contractor, End User, Fab/Manu, Galvanizer
- General Public, General Supplier, Govt/Local Auth
- Organic Coating/Supp, Prof Organisation, Steel Supplier
- Surveyor, Unspecified, Utilities

**Technical Requirements:**

- Real-time/near-real-time sync from Salesforce
- Bar and pie chart visualization
- Total count display
- Color-coded categories

#### 2. **Digital Comms - Website**

**Data Source:** Google Analytics

**Visualizations:**

- Website Traffic: Dual-axis bar chart (Sessions + Users) by month
- Publication Downloads: Bar chart by month
- Contact From Website: Bar chart by month

**Time Range:** January - August (monthly aggregation)

**Technical Requirements:**

- Scheduled sync from Google Analytics or Cloudflare
- Time-series bar charts
- Multiple metrics on same timeframe
- Monthly data aggregation

#### 3. **Steel/Construction Data**

**Data Source:** External industry data (manual entry)

**Visualizations:**

- Tables with multiple columns
- UK Steel Data: Volume, Y-o-Y change, Volume YTD
- Ireland Steel Data: Same structure
- Construction Data: Monthly value, % change, RSI

**Categories:**

- Steel: HR Sheet, CR Sheet, Coated Sheet, Rebar, Wire, All steel
- Construction: All Sectors, Commercial & Retail, Education, Hotel/Leisure, Industrial, Infrastructure, Medical & Healthcare, Residential

**Technical Requirements:**

- Manual data entry capability
- Multi-column table display
- Percentage formatting
- Decimal number handling

#### 4. **Standards Dashboard**

**Data Source:** Manual entry

**Visualizations:**

- Color-coded status table (Green/Amber/Red)
- Long-form text fields

**Fields:**

- Standard reference (e.g., EN ISO 14713-2:2020)
- Importance (text)
- Issue/Challenge (long text)
- Actions Taken (long text)
- Key Milestones (long text)

**Technical Requirements:**

- Conditional color coding
- Rich text/long text support
- Status indicator system
- Manual update capability

#### 5. **Digital Comms - Social**

**Data Source:** Sprout Social

**Visualizations:**

- Impressions: Bar chart (Jan-Aug)
- Engagement %: Bar chart (Jan-Aug)
- PLCs Post Link Clicks: Bar chart (Jan-Aug)

**Technical Requirements:**

- Manual data entry OR API integration
- Time-series visualization
- Percentage formatting
- Monthly aggregation

#### 6. **Inspections Dashboard**

**Data Source:** Salesforce OR manual entry

**Visualizations:**

- Bar chart: Inspections by type
- Pie chart: Distribution breakdown
- Total count display (11 inspections)

**Inspection Types:**

- Damage/Flaking, Service Finish, Colour Variation
- Wet Storage Stain, Rust/Staining, Distortion
- Coating Thickness, Fire Damage

**Technical Requirements:**

- Record counting
- Bar + pie chart visualization
- Color-coded categories

#### 7. **Environmental Dashboard**

**Data Source:** Manual entry

**Visualizations:**

- Color-coded status tracker (like Standards)
- Topics: UK BAT Conclusions, EU FMP BAT Conclusions

**Fields:**

- Topic/Title
- Importance
- Issue/Challenge
- Actions Taken
- Key Milestones

**Technical Requirements:**

- Identical to Standards dashboard
- Regulatory tracking
- Status color coding
- Long-form text support

#### 8. **CPD Dashboard**

**Data Source:** Salesforce

**Visualizations:**

- Table: CPD sessions by attendee type & month
- Bar chart: Total by business type

**Categories:**

- Engineer, Fabricator/Manufacturer
- Architect, Government/Local Authority

**Time Range:** January - August

**Technical Requirements:**

- Matrix/pivot table display
- Monthly breakdown
- Category aggregation
- Bar chart visualization

---

## Airtable Interface Capabilities Assessment

### ✅ Chart & Visualization Support

Airtable Interface Designer supports **ALL required visualization types**:

| Current Dashboard                | Airtable Equivalent                 | Availability |
| -------------------------------- | ----------------------------------- | ------------ |
| Bar Charts (vertical/horizontal) | ✅ Bar Chart                        | Native       |
| Pie Charts                       | ✅ Pie Chart                        | Native       |
| Donut Charts                     | ✅ Donut Chart                      | Native       |
| Line Charts                      | ✅ Line Chart                       | Native       |
| Multi-column Tables              | ✅ Grid Element / Pivot Table       | Native       |
| Number Displays                  | ✅ Number Element                   | Native       |
| Status Indicators                | ✅ Conditional Coloring             | Native       |
| Time-series Charts               | ✅ All chart types with date fields | Native       |

**Chart Configuration Options:**

- **X/Y axis configuration** for Bar, Line, Scatter charts
- **Category/Value configuration** for Pie/Donut charts
- **Stacking options**: None, Standard, 100% (for Bar charts)
- **Color customization**: Single select field OR conditional coloring
- **Size presets**: Small, Medium, Large
- **Click-through to underlying records**: Enabled/disabled
- **Filters and sorting**: Full support

### ✅ Data Table Support

**Grid Element:**

- Multi-column display
- Sortable columns
- Filterable rows
- Inline editing (configurable)
- Field visibility control

**Pivot Table:**

- Row and column grouping
- Multiple aggregation functions: Sum, Average, Min, Max, Count, Stdev, Variance, Median
- Show/hide totals
- Sort by group or value
- Conditional formatting

### ✅ Access Control & Permissions

**Interface-Level Permissions:**

- **Interface-only collaborators** (Team, Business, Enterprise plans)
- Users can view interfaces WITHOUT access to underlying base
- Requires verified Airtable account
- Permission levels: Owner, Creator, Editor, Commenter, Read-Only

**Field-Level Permissions:**

- Per-field editability control
- "Editable" vs "Read-only" settings
- Respects base-level field permissions

**Access Control Options:**

- **Public sharing**: Unrestricted access (with share link)
- **Email domain restriction**: Limit to specific domains
- **Password protection**: Paid plans only
- **Individual user invitations**: Granular control

**Perfect Match for Requirements:**

- ✅ Admin team: Edit access to update manual data
- ✅ Members: Read-only access via shareable link
- ✅ No need for members to access underlying base

### ✅ Data Integration Options

Airtable supports multiple data sync approaches:

**1. Native Integrations:**

- Salesforce (via Airtable sync or third-party)
- Google Analytics (via third-party connectors)
- Various automation platforms

**2. API Access:**

- RESTful API for all CRUD operations
- Webhooks for real-time updates
- OAuth for secure authentication

**3. n8n Integration** (RECOMMENDED):

- **Airtable nodes**: Native support for all operations
- **Salesforce nodes**: Query, create, update records
- **Google Sheets nodes**: Import GA data via scheduled exports
- **Scheduled workflows**: Daily/weekly data sync
- **Webhook triggers**: Real-time updates when needed

**4. Manual Entry:**

- Direct data entry via Airtable base OR interfaces
- CSV import
- Copy-paste from spreadsheets

---

## Recommended Architecture

### Data Model Design

**Base Structure:** Single Airtable Base with 8 tables (one per dashboard)

```
Member Dashboard Base
├── Enquiries (Table)
│   ├── Date (Date field)
│   ├── Category (Single select)
│   ├── Enquirer Type (Single select)
│   ├── Count (Number)
│   └── Salesforce ID (Text) [for sync tracking]
│
├── Website Metrics (Table)
│   ├── Month (Date field)
│   ├── Sessions (Number)
│   ├── Users (Number)
│   ├── Publication Downloads (Number)
│   └── Contact Form Submissions (Number)
│
├── Steel Data (Table)
│   ├── Country (Single select: UK, Ireland)
│   ├── Product Type (Single select: HR Sheet, CR Sheet, etc.)
│   ├── Month (Date field)
│   ├── Volume (Number)
│   ├── YoY Change % (Number)
│   ├── Volume YTD (Number)
│   └── YoY Change YTD % (Number)
│
├── Construction Data (Table)
│   ├── Sector (Single select)
│   ├── Month (Date field)
│   ├── Monthly Value £bn (Number)
│   ├── % Change (Number)
│   ├── RSI (Number)
│   └── Period (Single select: January, Q1, 2025, etc.)
│
├── Standards (Table)
│   ├── Standard Reference (Text)
│   ├── Status (Single select: Green, Amber, Red)
│   ├── Importance (Long text)
│   ├── Issue/Challenge (Long text)
│   ├── Actions Taken (Long text)
│   ├── Key Milestones (Long text)
│   └── Last Updated (Last modified time)
│
├── Social Media Metrics (Table)
│   ├── Month (Date field)
│   ├── Impressions (Number)
│   ├── Engagement % (Number)
│   ├── PLCs Post Link Clicks (Number)
│   └── Data Source (Single select: Sprout Social)
│
├── Inspections (Table)
│   ├── Date (Date field)
│   ├── Inspection Type (Single select)
│   ├── Count (Number)
│   └── Salesforce ID (Text)
│
├── Environmental (Table)
│   ├── Topic (Text)
│   ├── Status (Single select: Green, Amber, Red)
│   ├── Importance (Long text)
│   ├── Issue/Challenge (Long text)
│   ├── Actions Taken (Long text)
│   ├── Key Milestones (Long text)
│   └── Last Updated (Last modified time)
│
└── CPD Sessions (Table)
    ├── Month (Date field)
    ├── Business Type (Single select: Engineer, Fabricator, Architect, Gov/Local Auth)
    ├── Count (Number)
    └── Salesforce ID (Text)
```

### Interface Design

**8-Page Interface Structure:**

**Homepage/Dashboard Overview** (Optional):

- Quick summary numbers from all 8 sections
- Navigation cards to each dashboard section

**Page 1: Enquiries**

- Bar Chart: Enquiries by service line
- Pie Chart: Enquiries by enquirer type
- Number Element: Total enquiries (579)

**Page 2: Website**

- Bar Chart: Website traffic (Sessions + Users)
- Bar Chart: Publication downloads
- Bar Chart: Contact form submissions

**Page 3: Steel & Construction Data**

- Pivot Table: UK Steel Data
- Pivot Table: Ireland Steel Data
- Pivot Table: Construction Data

**Page 4: Standards**

- Grid Element: Standards with color-coded status
- Conditional coloring: Green/Amber/Red
- Click-through to record details for full text

**Page 5: Social Media**

- Bar Chart: Impressions
- Bar Chart: Engagement %
- Bar Chart: PLCs Post Link Clicks

**Page 6: Inspections**

- Bar Chart: Inspections by type
- Pie Chart: Distribution breakdown
- Number Element: Total inspections

**Page 7: Environmental**

- Grid Element: Environmental topics with status
- Conditional coloring: Green/Amber/Red
- Click-through to record details

**Page 8: CPD Sessions**

- Pivot Table: CPD by business type & month
- Bar Chart: Total by business type
- Number Element: Total CPD sessions

### Data Sync Architecture

**Automated Sync via n8n (Existing Subscription)**

**Salesforce → Airtable (Daily Sync)**

```
Trigger: Schedule (Daily at 1:00 AM)
├── Query Salesforce: Get new Enquiries records
├── Transform: Map SF fields to Airtable fields
├── Upsert to Airtable: Enquiries table (match on Salesforce ID)
│
├── Query Salesforce: Get new CPD records
├── Transform: Aggregate by month & business type
├── Upsert to Airtable: CPD Sessions table
│
└── Query Salesforce: Get new Inspections records
    ├── Transform: Map fields
    └── Upsert to Airtable: Inspections table
```

**Manual Data Entry**

Admin logs directly into Airtable base to update:

- **Website Metrics** (Google Analytics data)
- **Social Media Metrics** (Sprout Social data)
- **Steel Data** (External industry data)
- **Construction Data** (External industry data)
- **Standards** (Regulatory tracking)
- **Environmental** (Regulatory tracking)

Data entered in Airtable tables automatically reflects in published interface dashboards.

### Access Control Implementation

**Admin Team Access:**

- Single Airtable account with "Creator" permissions on Base
- Can edit all tables directly
- Can modify interfaces
- Can manage permissions
- Used by whoever needs to update manual data (Standards, Environmental, Steel Data)

**Member Access (Hundreds of Members):**

- Password-protected interface link
- Read-only access to published interfaces
- NO access to underlying base
- NO individual Airtable accounts required
- Single shared password for all members

**Share Link Configuration:**

```
Access Type: Password-protected (requires Team plan)
Password: [Set strong password for members]
Expiration: None (permanent access for members)
Public Link: Yes (anyone with link + password)
Advantages:
  - Unlimited members can access with one password
  - No individual account creation friction
  - Simple distribution (email link + password once)
```

---

## Implementation Approach

### Phase 1: Base Setup (Programmatic via MCP)

**Available Tools:**

- `mcp__MCP_DOCKER__create_table`: Create all 8 tables
- `mcp__MCP_DOCKER__create_field`: Define field schemas
- `mcp__MCP_DOCKER__create_record`: Populate sample data
- `mcp__MCP_DOCKER__list_bases`: Verify base creation

**Implementation Steps:**

1. Create new base: "Member Dashboard"
2. Create 8 tables with full field schemas (programmatically)
3. Set up field types, validation, and default values
4. Populate sample data for testing

### Phase 2: Manual Interface Configuration

**Note:** Airtable Interfaces cannot currently be created via API/MCP. This must be done via the Airtable web UI.

**Time Estimate:** 6-8.5 hours (~1 full working day)

**Steps:**

1. Open Interface Designer in Airtable
2. Create 8-page interface structure
3. Add visualizations (charts, grids, pivot tables)
4. Configure data sources and filters
5. Set up conditional coloring
6. Enable/disable user actions (click-through, editing)
7. Configure password protection and sharing settings

### Phase 3: Data Sync Setup

**n8n Workflows:**

1. Create Workflow 1: Salesforce → Airtable (Daily)
2. Create Workflow 2: Google Analytics → Airtable (Weekly)
3. Test all sync workflows with sample data
4. Set up error notifications

### Phase 4: Access Control & Testing

1. Configure interface sharing permissions
2. Invite admin team members (Creator access)
3. Create member shareable link (read-only)
4. Test access levels
5. Document access procedures

### Phase 5: Migration & Launch

1. Migrate historical data
2. Run parallel testing (old dashboard vs Airtable)
3. Train admin team on data updates
4. Launch to members
5. Deprecate old dashboard

---

## Technical Feasibility Assessment

### ✅ Fully Supported Features

| Requirement             | Airtable Capability           | Status          |
| ----------------------- | ----------------------------- | --------------- |
| Bar charts              | Native Bar Chart element      | ✅ Full support |
| Pie charts              | Native Pie Chart element      | ✅ Full support |
| Multi-column tables     | Grid Element + Pivot Table    | ✅ Full support |
| Color-coded status      | Conditional coloring          | ✅ Full support |
| Time-series data        | Date fields + chart filtering | ✅ Full support |
| Number displays         | Number Element                | ✅ Full support |
| Read-only member access | Interface-only collaborators  | ✅ Full support |
| Admin edit access       | Base Creator permissions      | ✅ Full support |
| Data sync automation    | API + n8n                     | ✅ Full support |
| Manual data entry       | Direct base editing           | ✅ Full support |

### ⚠️ Limitations & Considerations

**1. Interface Creation:**

- ❌ Cannot be automated via API
- ✅ Must be configured manually via Airtable UI
- Impact: Initial setup requires manual work, but only done once

**2. Paid Plan Required:**

- ❌ Interface-only collaborators require paid plan (Team, Business, or Enterprise)
- ✅ Core functionality works on free plan with different sharing approach
- Recommendation: Upgrade to Team plan (~$20/user/month)

**3. Real-Time Sync:**

- ❌ Not truly real-time (n8n runs on schedule)
- ✅ Near real-time possible with webhook triggers
- Recommendation: Daily sync sufficient for reporting dashboard

**4. Complex Calculations:**

- ⚠️ Limited formula complexity compared to Excel
- ✅ Sufficient for basic aggregations (sum, average, count)
- Recommendation: Pre-calculate complex metrics in n8n

**5. Design Customization:**

- ⚠️ Less design flexibility than custom HTML/CSS
- ✅ Professional, consistent Airtable design system
- ✅ Responsive out-of-box
- Impact: Slightly different look from current dashboard, but modern and professional

---

## Cost Analysis

### Airtable Pricing

**Team Plan** (Required for password protection):

- **€20/month** (single seat, annual billing)
- Includes:
  - Password-protected interface sharing
  - **Unlimited read-only viewers** (hundreds of members)
  - 50,000 records per base
  - 25,000 automation runs/month
  - 5GB attachments per base
  - Admin panel
  - Extended revision history

**Users Required:**

- 1 admin account: €20/month (edit access)
- Unlimited members: €0 (password-protected access, no accounts needed)

**Airtable Total Cost:** €20/month (~€240/year)

### n8n Pricing

**Existing Subscription:**

- Client already has active n8n subscription
- Existing workflows can be extended/modified
- **No additional cost**

**Data Sync Requirements:**

- Daily Salesforce sync (~300 operations/month)
- Weekly Google Analytics sync (~50 operations/month)
- Well within existing subscription limits

**n8n Additional Cost:** €0

### Total Project Cost

**Monthly:** €20/month (Airtable Team plan only)
**Annual:** ~€240/year

**Cost Savings vs Custom Development:**

- No developer maintenance costs
- No hosting infrastructure costs
- No additional data sync platform costs
- Replaces potentially expensive custom extranet hosting

---

## Conclusion

**Airtable is fully capable of replicating and enhancing the current member dashboard.** All required visualization types, data structures, and access controls are natively supported. The combination of Airtable Interfaces + n8n data sync provides a robust, maintainable solution.

**Key Advantages:**

- ✅ Native support for all current visualizations
- ✅ Superior access control (interface-only members)
- ✅ Programmatic base setup via MCP
- ✅ Lower total cost than custom development
- ✅ Admin-friendly manual data entry
- ✅ Scalable for future enhancements

**Recommended Decision:** Proceed with Airtable implementation.

**Estimated Timeline:** 1-2 weeks

- Base setup (programmatic): 1-2 hours
- Interface configuration (manual): 1 working day
- n8n sync setup: 4-6 hours
- Testing & refinement: 2-3 hours
- Documentation: 2-3 hours
- **Total effort: ~15-22 hours** spread over 1-2 weeks

---

## Appendix

### Technical Resources

- [Airtable Interface Designer Documentation](https://support.airtable.com/docs/getting-started-with-airtable-interface-designer)
- [Airtable API Documentation](https://airtable.com/developers/web/api/introduction)
- [n8n Airtable Integration](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.airtable/)
- [n8n Salesforce Integration](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.salesforce/)

### MCP Tool Reference

```javascript
// Available Airtable MCP Tools
mcp__MCP_DOCKER__list_bases();
mcp__MCP_DOCKER__list_tables(baseId);
mcp__MCP_DOCKER__describe_table(baseId, tableId);
mcp__MCP_DOCKER__create_table(baseId, name, fields);
mcp__MCP_DOCKER__create_field(baseId, tableId, field);
mcp__MCP_DOCKER__create_record(baseId, tableId, fields);
mcp__MCP_DOCKER__list_records(baseId, tableId, filters);
mcp__MCP_DOCKER__update_records(baseId, tableId, records);
mcp__MCP_DOCKER__delete_records(baseId, tableId, recordIds);
mcp__MCP_DOCKER__search_records(baseId, tableId, searchTerm);
```

### Color Coding Standards

**Status Colors (Standards & Environmental):**

- 🟢 **Green (Satisfactory):** #10B981
- 🟡 **Amber (Challenge Presented):** #F59E0B
- 🔴 **Red (Critical Challenge Presented):** #EF4444

**Chart Colors (Recommendation):**

- Use Airtable's built-in color palettes
- Maintain consistency across all dashboards
- Ensure accessibility (WCAG AA contrast ratios)

---

**Document Status:** Complete
**Review Required:** Product Owner, Technical Lead
**Next Action:** Proceed to Product Requirements Document (PRD)
