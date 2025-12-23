# IMDB Database Systems Project - README

**Course:** CSE323 - Advanced Database Systems  
**Institution:** King Salman International University  
**Project Type:** Team Project (3 Members)  
**Submitted:** December 2025

---

## 📋 Project Overview

This project involves designing, implementing, and optimizing a PostgreSQL database using the IMDb (International Movie Database) dataset. The database includes 6 core tables (Titles, Names, Ratings, Principals, Crew, Episodes) and covers advanced database concepts including indexing, query optimization, transactions, concurrency control, backup/recovery, and security.

**Total Points:** 10  
**Original Due Date:** December 22, 2025  
**Current Status:** IN PROGRESS

---

## 👥 Team Members

| # | Name | ID | Role | Status |
|---|------|----|----|--------|
| 1 | [Member 1] | [ID] | [Lead/Developer] | ✅ Active |
| 2 | [Member 2] | [ID] | [Developer] | ✅ Active |
| 3 | [Member 3] | [ID] | [Developer] | ✅ Active |

---

## 📅 Project Timeline & Milestones

### Phase 1: Database Setup (Dec 6 - Dec 10)
| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Download IMDB dataset | Dec 6 | ✅ Complete | 6 TSV files (~50GB) |
| Schema design & analysis | Dec 7 | ✅ Complete | 6 tables defined |
| Database creation (PostgreSQL) | Dec 8 | ✅ Complete | All tables created |
| Data import | Dec 9 | 🔄 In Progress | Resolved COPY permission errors |
| Query verification (1c-1f) | Dec 10 | ⏳ Pending | Awaiting data load completion |

### Phase 2: Indexing & Optimization (Dec 11 - Dec 15)
| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Create basic B-tree indexes | Dec 11 | 🔄 In Progress | Title, name, rating indexes |
| Test GIN indexes (full-text) | Dec 12 | ⏳ Pending | Text search optimization |
| Test BRIN indexes | Dec 12 | ⏳ Pending | Large table efficiency |
| Task 2d: Composite index comparison | Dec 13 | ⏳ Pending | titleType + startYear |
| Task 2e: Text search analysis | Dec 14 | ⏳ Pending | LIKE vs GIN performance |
| Task 2f: Insert performance test | Dec 15 | ⏳ Pending | 1000 record benchmark |

### Phase 3: Query Optimization (Dec 15 - Dec 18)
| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Christopher Nolan query (3 versions) | Dec 16 | ⏳ Pending | Subquery → CTE → Optimized |
| Given inefficient query optimization | Dec 17 | ⏳ Pending | 30sec → <5sec target |
| Performance comparison & analysis | Dec 18 | ⏳ Pending | EXPLAIN ANALYZE results |

### Phase 4: Advanced Concepts (Dec 18 - Dec 20)
| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Task 4: Subqueries vs JOINs | Dec 18 | ⏳ Pending | NOT IN vs LEFT JOIN vs NOT EXISTS |
| Task 5: Functions | Dec 19 | ⏳ Pending | Episode counting, ID generation |
| Task 6: Transactions & ACID | Dec 19 | ⏳ Pending | Lost update problem demonstration |
| Task 7: Concurrency control | Dec 20 | ⏳ Pending | Isolation levels & deadlock handling |

### Phase 5: Production Readiness (Dec 20 - Dec 22)
| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Task 8: Backup & Recovery | Dec 21 | ⏳ Pending | WAL, point-in-time recovery |
| Task 9: Security (RBAC, encryption) | Dec 22 | ⏳ Pending | Roles, RLS, audit logging |
| Database dump export | Dec 22 | ⏳ Pending | .dump or .sql format |
| Report compilation | Dec 22 | ⏳ Pending | Design doc + performance metrics |
| Final deliverable (.zip/.rar) | Dec 22 | ⏳ Pending | All files packaged |

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

## 🔧 Technical Stack

| Component | Version | Status |
|-----------|---------|--------|
| PostgreSQL | 15.x+ | ✅ Installed |
| pgAdmin 4 | Latest | ✅ Installed |
| psql CLI | v15+ | ✅ Ready |
| Python 3.x | 3.8+ | ⏳ Optional (for benchmarking) |
| IMDb Dataset | Current | ✅ Downloaded |

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

---

## 📞 Communication & Updates

- **Last Updated:** December 15, 2025, 2:26 PM EET
- **Next Milestone:** Complete Task 2 (Indexes) by Dec 16
- **Final Submission:** December 23, 2025 (revised)

---

**Good luck with the project! 🚀**
