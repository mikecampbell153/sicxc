# SICXC Race Management System

## Overview

The SICXC Race Management System is a web application developed to support a middle school cross country program by tracking athletes, races, performances, and training plans.

The application was built to solve several common challenges faced by coaches and team volunteers:

- Maintaining athlete race histories across multiple seasons
- Recording and analyzing race results
- Tracking personal records and team records
- Managing meet schedules and results
- Supporting weekly training plans
- Providing simple reporting and lookup functionality for athletes and coaches

The system uses a PostgreSQL database to store athlete and race data and was originally hosted using resources available through an Office 365 Personal Azure environment.

---

## Key Features

### Athlete Management

- Store athlete information and race history
- Track participation across multiple meets
- Query athlete performance over time

### Meet Management

- Create and manage race meet entries
- Lookup meet information
- Query meet results and participation

### Performance Tracking

- Record official race times
- Maintain athlete records and historical results
- Compare performances across races and seasons

### Training Plan Management

- Create weekly training plans
- Track workout schedules
- Maintain season training records

### Reporting and Lookup

- Athlete performance lookups
- Meet result searches
- Historical record reporting
- Performance analysis queries

---

## Technical Stack

### Front End

- ASP.NET Web Forms (`.aspx`)

### Database

- PostgreSQL

### Hosting

- Azure services associated with an Office 365 Personal subscription

---

## Database Design

The database was intentionally designed to be simple and highly queryable.

Example data elements included:

- Athlete Name
- Meet/Race Name
- Race Date
- Race Time
- Training Plan Information
- Historical Records

### Race Time Storage

One of the primary design decisions involved race time storage.

Rather than storing race results as traditional time values, race times were stored as:

```text
seconds.milliseconds
```

Examples:

```text
1023.45
1087.92
1205.31
```

This approach avoided issues commonly encountered when importing and exporting data through Microsoft Excel, where race times may be interpreted inconsistently as:

- `h:mm:ss`
- `mm:ss`
- duration values
- date/time values

By storing race performance as a numeric value representing total elapsed seconds, calculations, sorting, ranking, and reporting became significantly more reliable and database-friendly.

---

## Project Structure

| File | Purpose |
|--------|---------|
| `sicxc.aspx` | Main application page |
| `sicxcquery.aspx` | Athlete and race query functionality |
| `sicxcmeets.aspx` | Meet management |
| `sicxcmeetslookup.aspx` | Meet lookup interface |
| `sicxcmeetsquery.aspx` | Meet reporting and queries |
| `sicmeetslookup.aspx` | Additional meet lookup functions |
| `sicxcrecords.aspx` | Historical records and personal records |
| `TrainingPlan.aspx` | Training plan management |
| `trainingplaninsert.aspx` | Training plan entry screen |
| `trainingplanweek.aspx` | Weekly training plan display |
| `postgres.sql` | PostgreSQL database schema and scripts |

---

## Installation

### Prerequisites

- PostgreSQL
- IIS
- ASP.NET Framework
- Visual Studio (optional for development)
- Notepad++ (my preferred IDE) 

### Database Setup

Create the PostgreSQL database and execute:

```sql
postgres.sql
```

to create the required tables, indexes, and supporting objects.

### Application Deployment

1. Clone the repository.
2. Configure database connection strings.
3. Deploy the ASP.NET application to IIS.
4. Verify database connectivity.
5. Navigate to the application's home page.

---

## Purpose

This project was developed as a practical tool to support a middle school cross country team. Rather than focusing on enterprise-scale architecture, the emphasis was on reliability, quick data entry, effective reporting, and preserving historical race performance data in a format that coaches and volunteers could easily maintain.

---

## Future Enhancements

Potential improvements include:

- Athlete dashboards
- Team performance analytics
- Automated personal record tracking
- Season-over-season trend analysis
- Mobile-friendly user interface
- Integration with official race timing platforms
- Data export to Excel and Power BI

---

## License

This project is provided as-is for educational and personal-use purposes.

## Author

Developed to support youth cross country athletics and simplify race-performance tracking, reporting, and training-plan management.
