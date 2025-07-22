Analyze GitHub repository contributor trends, value metrics, and code churn patterns using GitHub CLI and git commands.

## Required Actions:
1. Use GitHub CLI (`gh`) and `git` commands to gather comprehensive contributor data
2. Analyze commit patterns, code churn, and contributor value metrics
3. Generate a structured markdown report with actionable insights

## Data Collection Commands to Execute:
```bash
# Get repository information
gh repo view --json name,owner,createdAt,pushedAt,stargazerCount,forkCount

# Get contributor statistics (last 12 months)
gh api repos/:owner/:repo/stats/contributors

# Get recent commits with detailed stats
git log --since="12 months ago" --pretty=format:"%H|%an|%ae|%ad|%s" --date=short --numstat

# Get commit activity by author (last 6 months)
git shortlog -sn --since="6 months ago"

# Get file change frequency
git log --since="6 months ago" --name-only --pretty=format: | sort | uniq -c | sort -rn | head -20

# Get contributor commit frequency over time
git log --since="12 months ago" --pretty=format:"%an %ad" --date=short | sort | uniq -c
```

## Report Format Required:

### Executive Summary
- Repository overview (name, age, stars, forks)
- Total active contributors (last 12 months)
- Total commits analyzed
- Date range covered
- Top contributor identification
- Repository health score assessment
- Bus factor analysis (contributor dependency risk)

### Contributor Rankings Table
A markdown table with top 15 contributors showing:
- Contributor name
- Total commits (last 12 months)
- Lines added (thousands, e.g., 12,345 as 12.3k)
- Lines deleted (thousands)  
- Net contribution (added - deleted)
- Files touched
- Average commit size
- First contribution date
- Last contribution date
- Contribution consistency score

### Code Churn Analysis
- **High Churn Files**: Files with most frequent changes
- **Churn by Contributor**: Who creates most churn vs. who creates stable code
- **Refactoring Patterns**: Large deletions indicating cleanup work
- **Code Stability**: Files with low churn but high importance

### Temporal Analysis
#### Monthly Contribution Trends
- Commits per month over last 12 months
- Active contributors per month
- New contributors joining
- Contributors going inactive

#### Contribution Patterns
- Peak activity days/times
- Weekend vs. weekday activity
- Seasonal patterns in contributions

### Contributor Value Metrics
#### Impact Assessment
- **High Impact Contributors**: Large, meaningful commits with low revert rate
- **Maintenance Contributors**: Consistent small fixes and improvements
- **Feature Contributors**: Large feature additions
- **Documentation Contributors**: README, docs, comment improvements

#### Specialization Analysis
- File type expertise (frontend/backend/config/docs)
- Component ownership patterns
- Cross-functional vs. specialized contributors

### Repository Health Insights
#### Diversity Metrics
- Contributor distribution (% of commits by top 5/10 contributors)
- Geographic distribution (if email domains indicate)
- Contribution recency distribution

#### Sustainability Assessment
- **Bus Factor**: Risk assessment if top contributors leave
- **Knowledge Concentration**: Areas with single-contributor expertise
- **Onboarding Success**: New contributor retention and growth
- **Maintenance Load**: Ratio of feature work to maintenance work

### Code Quality Indicators
- Average commit message quality (length, descriptiveness)
- Commit size distribution (small focused vs. large commits)
- File coupling analysis (files frequently changed together)
- Hotspot identification (files changed by many contributors)

### Actionable Recommendations
Based on the analysis, provide:
- **Contributor Recognition**: Who should be acknowledged for impact
- **Knowledge Sharing**: Areas needing documentation or cross-training
- **Process Improvements**: Patterns suggesting workflow optimizations
- **Team Health**: Onboarding, retention, and sustainability recommendations
- **Technical Debt**: Files or areas needing attention based on churn patterns

### Visual Data Representations
Include ASCII charts or structured tables for:
- Monthly commit timeline
- Contributor activity heatmap (text-based)
- Top file change frequency
- Commit size distribution

## Output Requirements:
- Format everything in clean, readable markdown
- Use proper tables with aligned columns
- Include summary statistics with context
- Focus on actionable insights for project management
- Highlight both positive patterns and areas of concern
- Provide specific recommendations based on data patterns

## Analysis Notes:
- Consider commit message quality and consistency
- Identify potential bottlenecks or single points of failure
- Look for signs of healthy collaboration vs. isolated work
- Assess whether contributors are growing in scope and impact over time
- Note any unusual patterns that might indicate tooling or process issues