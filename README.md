# IMDB Database Systems Project - README

**Course:** CSE323 - Advanced Database Systems  
**Institution:** King Salman International University  
**Submitted:** December 2025

---

## 📋 Project Overview

This project involves designing, implementing, and optimizing a PostgreSQL database using the IMDb (International Movie Database) dataset. The database includes 6 core tables (Titles, Names, Ratings, Principals, Crew, Episodes) and covers advanced database concepts including indexing, query optimization, transactions, concurrency control, backup/recovery, and security.

**Current Status:** IN PROGRESS

---

## 📅 Project Timeline & Milestones

### Phase 1: Database Setup (Dec 20 - Dec 22)
| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Download IMDB dataset | Dec 20-22 | ✅ Complete | 6 TSV files (~50GB) |
| Schema design & analysis | Dec 20-22 | ✅ Complete | 6 tables defined |
| Database creation (PostgreSQL) | Dec 20-22 | ✅ Complete | All tables created |
| Data import | Dec 20-22 | ✅ Completed | Resolved COPY permission errors |
| Query verification (1c-1f) | Dec 20-22 | ✅ Completed | Awaiting data load completion |

### Phase 2: Indexing & Optimization (Dec 23 - Dec 25)
| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Create basic B-tree indexes | Dec 23-25 | 🔄 In Progress | Title, name, rating indexes |
| Test GIN indexes (full-text) | Dec 23-25 | ⏳ Pending | Text search optimization |
| Test BRIN indexes | Dec 23-25 | ⏳ Pending | Large table efficiency |
| Task 2d: Composite index comparison | Dec 23-25 | ⏳ Pending | titleType + startYear |
| Task 2e: Text search analysis | Dec 23-25 | ⏳ Pending | LIKE vs GIN performance |
| Task 2f: Insert performance test | Dec 23-25 | ⏳ Pending | 1000 record benchmark |

### Phase 3: Query Optimization (Dec 26 - Dec 28)
| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Christopher Nolan query (3 versions) | Dec 26-28 | ⏳ Pending | Subquery → CTE → Optimized |
| Given inefficient query optimization | Dec 26-28 | ⏳ Pending | 30sec → <5sec target |
| Performance comparison & analysis | Dec 26-28 | ⏳ Pending | EXPLAIN ANALYZE results |

### Phase 4: Advanced Concepts (Dec 29 - Dec 31)
| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Task 4: Subqueries vs JOINs | Dec 29-31 | ⏳ Pending | NOT IN vs LEFT JOIN vs NOT EXISTS |
| Task 5: Functions | Dec 29-31 | ⏳ Pending | Episode counting, ID generation |
| Task 6: Transactions & ACID | Dec 29-31 | ⏳ Pending | Lost update problem demonstration |
| Task 7: Concurrency control | Dec 29-31 | ⏳ Pending | Isolation levels & deadlock handling |

### Phase 5: Production Readiness (Jan 1 - Jan 3)
| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Task 8: Backup & Recovery | Jan 1-3 | ⏳ Pending | WAL, point-in-time recovery |
| Task 9: Security (RBAC, encryption) | Jan 1-3 | ⏳ Pending | Roles, RLS, audit logging |
| Database dump export | Jan 1-3 | ⏳ Pending | .dump or .sql format |
| Report compilation | Jan 1-3 | ⏳ Pending | Design doc + performance metrics |
| Final deliverable (.zip/.rar) | Jan 1-3 | ⏳ Pending | All files packaged |

---

## 🎯 Current Status Summary

### Completed ✅
- [x] IMDB dataset downloaded (6 TSV files)
- [x] Database schema designed (6 tables with constraints)
- [x] PostgreSQL database created
- [x] Foreign key relationships defined
- [x] Initial table creation completed

### In Progress 🔄
- [x] Data import (resolved COPY permission issues)
  - Error: "Permission denied" on OneDrive files
  - Solution: Using `\copy` client-side command from psql
  - Error: Column mapping (genres vs runtimeMinutes)
  - Solution: Corrected table schema and COPY syntax
- [ ] Data validation and cleanup
- [ ] Index creation and testing

### Pending ⏳
- [ ] All Task 2-9 implementation and testing
- [ ] Performance metrics collection
- [ ] Report generation
- [ ] Final packaging and submission

---

## 📁 Project Structure

```
CSE323-Project/
├── README.md (this file)
├── SQL Scripts/
│   ├── 01-schema-creation.sql          (Task 1)
│   ├── 02-indexes.sql                  (Task 2)
│   ├── 03-query-optimization.sql       (Task 3)
│   ├── 04-subqueries.sql              (Task 4)
│   ├── 05-functions.sql               (Task 5)
│   ├── 06-transactions.sql            (Task 6)
│   ├── 07-concurrency-control.sql     (Task 7)
│   ├── 08-backup-recovery.sql         (Task 8)
│   └── 09-security.sql                (Task 9)
├── Reports/
│   ├── DESIGN_DOCUMENT.md
│   ├── PERFORMANCE_METRICS.md
│   └── OPTIMIZATION_ANALYSIS.md
├── Database Dumps/
│   ├── imdb_database.dump              (Compressed backup)
│   └── imdb_database.sql               (SQL format)
└── Documentation/
    ├── IMDB-DB-Complete-Guide.md       (Implementation walkthrough)
    └── TROUBLESHOOTING.md
```

---

## 🚨 Known Issues & Blockers

### Issue 1: Data Import Permission Error (RESOLVED ✅)
**Status:** Resolved  
**Error:** `ERROR: could not open file "C:\Users\...\OneDrive\...\title.basics.tsv" for reading: Permission denied`  
**Root Cause:** PostgreSQL server process cannot access OneDrive user folder  
**Solution:** 
- Move IMDB files to `C:\imdb\` (outside OneDrive)
- Use `\copy` client-side command from psql instead of server-side `COPY`
- Granted read permissions to PostgreSQL service account

### Issue 2: COPY Syntax Error (RESOLVED ✅)
**Status:** Resolved  
**Error:** `ERROR: syntax error at or near ""C:/imdb/title.basics.tsv""`  
**Root Cause:** Double quotes used for file path instead of single quotes  
**Solution:** Changed `FROM "path"` to `FROM 'path'`

### Issue 3: Column Mapping Error (RESOLVED ✅)
**Status:** Resolved  
**Error:** `ERROR: invalid input syntax for type integer: "Animation,Comedy"`  
**Root Cause:** Table schema missing `genres` column or COPY column list incomplete  
**Solution:** 
- Verified all 9 columns present in correct order
- Used full column list in COPY statement
- Confirmed genre data mapping correctly

### Issue 4: pg_indexes Query Error (RESOLVED ✅)
**Status:** Resolved  
**Error:** `ERROR: column "indexrelid" does not exist`  
**Root Cause:** `pg_indexes` view doesn't have `indexrelid`; it's in `pg_index` table  
**Solution:** Changed `indexrelid` to `indexname::regclass`

### Issue 5: pg_stat_user_tables Query Error (RESOLVED ✅)
**Status:** Resolved  
**Error:** `ERROR: column "relkind" does not exist`  
**Root Cause:** `relkind` is in `pg_class`, not `pg_stat_user_tables`  
**Solution:** Removed `relkind` from query; included in alternative queries joining `pg_class`

---

## ✨ Key Achievements

✅ **Dec 6-8:** Successful database schema design and creation  
✅ **Dec 9:** Resolved data import permission issues (3 errors fixed)  
✅ **Dec 14:** Created comprehensive 4000+ line implementation guide  
✅ **Dec 15:** Fixed query syntax errors and performance analysis queries  

---

## 📊 Performance Targets (Task 2-3)

| Optimization | Target | Status |
|--------------|--------|--------|
| Query optimization (inefficient query) | <5 seconds | ⏳ Testing |
| Composite index speedup | 2-3x faster | ⏳ Testing |
| Text search (GIN index) | <1 second | ⏳ Testing |
| Insert performance impact | <10% overhead | ⏳ Testing |

---

## 📝 Important Notes

1. **File Locations:**
   - IMDB dataset: `C:\imdb\` (moved from OneDrive)
   - SQL scripts: `/SQL Scripts/` folder
   - Database dumps: `/Database Dumps/` folder

2. **Team Responsibilities:**
   - Member 1: Schema design, Tasks 1-3
   - Member 2: Functions, Transactions, Concurrency (Tasks 5-7)
   - Member 3: Backup, Security, Reporting (Tasks 8-9)

3. **Deadline Extension:**
   - Original: December 22, 2025
   - Current: Still working (Dec 23+)
   - Focus: Complete Tasks 2-9 with comprehensive testing

4. **Report Requirements:**
   - Database design documentation
   - Performance comparison metrics (before/after optimization)
   - Analysis of each optimization technique
   - Security and recovery strategy evaluation

---

## 🔗 References & Resources

- **PostgreSQL Documentation:** https://www.postgresql.org/docs/current/
- **IMDB Dataset:** https://datasets.imdbws.com/
- **Implementation Guide:** `IMDB-DB-Complete-Guide.md`
- **Course Materials:** CSE323 Advanced Database Systems

---

## 📋 Deliverables Checklist

- [ ] Database schema creation scripts
- [ ] All 9 task implementation files
- [ ] Performance metrics and benchmarks
- [ ] Detailed technical report (PDF)
- [ ] PostgreSQL database dump
- [ ] Security implementation documentation
- [ ] Backup & recovery procedure documentation
- [ ] Compressed archive (.zip/.rar)
  - Format: `ID#1_Name#1_ID#2_Name#2_ID#3_Name#3_CSE323-Project.rar`

---

## 🎬 Getting Started (For Team Members)

### 1. Clone/Access Project Files
```bash
cd C:\path\to\CSE323-Project
```

### 2. Prepare Database
```sql
-- In psql:
\c imdb_database

-- Run setup scripts in order:
\i 'SQL Scripts/01-schema-creation.sql'
\i 'SQL Scripts/02-indexes.sql'
-- ... continue with Tasks 2-9
```

### 3. Run Benchmarks
```sql
-- From: SQL Scripts/02-indexes.sql
-- Execute EXPLAIN ANALYZE queries and record timing
```

### 4. Generate Report
```bash
# Compile all findings into final report
# Include metrics, analysis, and recommendations
```

