# Building a Multi-Organization Testing Platform in Moodle: Complete Beginner's Guide

## What We're Building (Simple Overview)

Imagine you're creating a **digital testing center** where multiple companies can come to test their employees. Each company has different types of workers (IT, HR, Finance, etc.) who need to take different tests. Your Moodle site will be like a **virtual building** with separate floors for each company, and different rooms for different subjects.

## Key Moodle Concepts You Need to Know

Before we start, let's understand the basic building blocks:

| Moodle Term | Real-World Equivalent | What It Does |
|-------------|----------------------|--------------|
| **Category** | Building floors/departments | Groups courses together (we'll use this for organizations) |
| **Course** | Individual classrooms | Contains lessons and tests for one subject |
| **Section/Topic** | Units within a classroom | Breaks a subject into smaller parts |
| **Quiz** | Individual tests | The actual exams employees take |
| **Cohort** | Employee groups | Groups users together (like "IT Department") |
| **User Profile Fields** | Employee ID cards | Stores extra info about users (like their specialization) |

## Visual Structure of What We're Building

```
🏢 MOODLE SITE: "Multi-Org Testing Center"
│
├── 🏬 Company A (Category)
│   ├── 👥 Groups: CompanyA-IT, CompanyA-HR, CompanyA-Finance (Cohorts)
│   ├── 📚 IT Fundamentals (Course/Subject)
│   │   ├── 📖 Unit 1: Basics (Section)
│   │   │   └── 📝 Quiz 1: Basic IT Test
│   │   └── 📖 Unit 2: Advanced (Section)
│   │       └── 📝 Quiz 2: Advanced IT Test
│   ├── 📚 HR Policies (Course/Subject)
│   └── 📁 Company A Documents (Special course for file uploads)
│
├── 🏬 Company B (Category) 
│   ├── 👥 Groups: CompanyB-IT, CompanyB-Marketing
│   ├── 📚 Same subjects, different access
│   └── 📁 Company B Documents
│
└── 🏬 Company C (Category)
    └── (Similar structure...)
```

## Step-by-Step Implementation Guide

### Phase 1: Setting Up the Foundation (Week 1)

#### Step 1.1: Install and Access Moodle
- **For beginners**: Use a free hosting service like MoodleCloud.com or install on a local computer using XAMPP
- Log in as **Site Administrator** (the master account)

#### Step 1.2: Create the Main Structure
1. **Go to**: Site administration → Courses → Manage courses and categories
2. **Create a main category** called "Testing Organizations"
3. **Under this, create subcategories** for each organization:
   - Right-click "Testing Organizations" → Add subcategory
   - Name it "Company-A", "Company-B", etc.

#### Step 1.3: Set Up User Information Fields
1. **Go to**: Site administration → Users → User profile fields
2. **Add custom fields**:
   - Field name: "Organization" (Text input)
   - Field name: "Specialization" (Menu of choices: IT, HR, Finance, Marketing)
   - Field name: "Employee ID" (Text input)

### Phase 2: Creating the Course Templates (Week 2)

#### Step 2.1: Build Your First Subject Template
1. **Go to your Company-A category**
2. **Add a new course**: "IT Fundamentals - Template"
3. **Inside the course**:
   - Turn editing on (top right)
   - Rename "Topic 1" to "Unit 1: IT Basics"
   - Add a Quiz activity: "Unit 1 Quiz"
   - Add "Topic 2" and rename to "Unit 2: Advanced IT"
   - Add another Quiz: "Unit 2 Quiz"

#### Step 2.2: Create Question Banks
1. **In your course**: Go to the Quiz → Questions tab
2. **Create categories** for your questions:
   - "IT-Unit1-Questions"
   - "IT-Unit2-Questions"
3. **Add sample questions** to each category

### Phase 3: Setting Up Organization Management (Week 3)

#### Step 3.1: Create Cohorts (Employee Groups)
1. **Go to**: Site administration → Users → Cohorts
2. **For each organization, create cohorts**:
   - "CompanyA-IT" 
   - "CompanyA-HR"
   - "CompanyA-Finance"
3. **Set the context** to the appropriate category (Company-A)

#### Step 3.2: Set Up Automatic Enrollment
1. **Go to each course** (like "IT Fundamentals")
2. **Click "Participants"** → Enrolment methods
3. **Add "Cohort sync"** enrollment method
4. **Select the appropriate cohort** (CompanyA-IT for IT course)
5. **Set role to "Student"**

### Phase 4: Document Upload System (Week 3-4)

#### Step 4.1: Create Document Upload Courses
1. **For each organization**, create a special course: "Company-A Documents"
2. **Make it hidden** from students (Course settings → Course visibility → Hide)
3. **Add an Assignment activity**:
   - Assignment name: "Upload Exam Materials"
   - Submission types: File submissions
   - Maximum number of files: 20

#### Step 4.2: Create Organization Admin Role
1. **Go to**: Site administration → Users → Permissions → Define roles
2. **Create new role**: "Organization Manager"
3. **Give permissions**:
   - Can upload files to assignments
   - Can enroll users in courses within their category
   - Can view reports for their category only

### Phase 5: Bulk User Management (Week 4-5)

#### Step 5.1: Prepare CSV Template
Create a spreadsheet with these columns:
```
username,firstname,lastname,email,organization,specialization,cohort1
jsmith,John,Smith,john@companya.com,Company-A,IT,CompanyA-IT
mjones,Mary,Jones,mary@companya.com,Company-A,HR,CompanyA-HR
```

#### Step 5.2: Bulk Upload Process
1. **Organization admin goes to**: Site administration → Users → Upload users
2. **Upload the CSV file**
3. **Moodle automatically**:
   - Creates user accounts
   - Assigns them to cohorts based on specialization
   - Enrolls them in appropriate courses

### Phase 6: Testing and Automation (Week 5-6)

#### Step 6.1: Test the Full Workflow
1. **Create a test organization**: "Test-Company"
2. **Upload sample employees** with different specializations
3. **Verify they can access only their assigned courses**
4. **Test the quiz-taking experience**

#### Step 6.2: Set Up Reporting
1. **Install free plugin**: "Configurable Reports" from moodle.org/plugins
2. **Create reports for**:
   - Employee test scores by organization
   - Course completion rates
   - Organization-specific analytics

## Free Tools and Plugins You'll Need

| Tool/Plugin | Purpose | Where to Get It |
|-------------|---------|-----------------|
| **Moodle Core** | Basic platform | moodle.org (free download) |
| **Cohort Sync** | Auto-enrollment | Built into Moodle |
| **Configurable Reports** | Custom reporting | moodle.org/plugins |
| **Course Copies** | Duplicate course templates | Built into Moodle |
| **CSV Upload** | Bulk user management | Built into Moodle |

## Beginner-Friendly Tips

### 🔧 **Getting Started Tips**
- **Start small**: Begin with one organization and one subject
- **Use the sandbox**: Create test accounts to practice
- **Backup frequently**: Use Moodle's built-in backup before making changes

### 🚨 **Common Mistakes to Avoid**
- Don't edit Moodle core files (you'll lose changes on updates)
- Always test user permissions with dummy accounts
- Keep your categories organized from the start

### 🎯 **Success Metrics**
- Organizations can upload documents easily
- Employees automatically see only their assigned courses
- Quiz results are properly tracked by organization
- System handles multiple simultaneous users

## Simple 30-Day Implementation Timeline

**Days 1-7**: Set up Moodle, create categories, and build one complete course template
**Days 8-14**: Create cohorts, set up auto-enrollment, and test with sample users  
**Days 15-21**: Build document upload system and organization admin roles
**Days 22-28**: Test full workflow with multiple organizations
**Days 29-30**: Set up reporting and train organization administrators

## Next Steps After Implementation

1. **Train organization administrators** on uploading documents and managing employees
2. **Create user manuals** with screenshots for common tasks
3. **Set up regular backups** and update schedules
4. **Monitor system performance** as more organizations join
5. **Collect feedback** and iterate on the user experience

This system will give you a professional, scalable testing platform that organizations can use independently while maintaining complete separation of their data and users. The best part? It's built entirely with free, open-source tools!