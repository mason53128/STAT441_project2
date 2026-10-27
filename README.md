# Project 2 Checklist: Were the 2025–26 Knicks an Anomaly?
 
**Report + presentation + code due: Friday, November 6, 12:00 pm (noon)**
**Peer reviews due: Friday, November 13, 12:00 pm (noon)**
 
Team ID: `__` (two digits; goes in every file name)
 
---
 
## 1. Model and simulation (`knicks_bradley_terry.qmd`)
 
### Data
- [x] Load 2025–26 regular-season results (`hoopR::load_nba_schedule(2026)`)
- [x] Drop All-Star / Rising Stars games
- [x] Drop the NBA Cup Championship game (keep group play and QF/SF, which count toward the 82)
- [x] Drop 0–0 placeholder rows for postponed games
- [ ] **Re-render and confirm `1230 games loaded` and all 30 teams at 82 games (`table(gp)`)**
### Model
- [x] Bradley-Terry model with home-court advantage, fit as a logistic regression
- [x] Team ratings table and home-court estimate
- [x] Calibration check (model-expected wins vs. actual wins)
- [ ] *(Encouraged by the assignment)* Test whether latent strength varies with covariates, e.g. team offensive/defensive rating, using `BradleyTerry2`. Compare to the plain model.
### Simulation
- [x] Simulate the full 1,230-game regular season
- [x] Conference seeding (random tiebreaks)
- [x] Play-in tournament (7v8, 9v10, loser vs. winner)
- [x] Best-of-7 playoffs with 2-2-1-1-1 home court, through the Finals
- [x] Parameter uncertainty (fresh ratings drawn each simulation)
- [x] At least 10,000 replications (`N_SIMS <- 10000`, which is above the 500 minimum)
- [x] Keep every team's result in every sim (`wins`, `conf_rank`, `playoff_seed`, `rounds_won`)
- [x] Save results to `nba_sims_2026.rds`
- [x] Integrity checks (one champion per sim, 8 playoff teams per conference)
- [ ] Run on the real data and check the output looks sensible (e.g. title probabilities sum to 100%)
- [ ] Set and report a fixed seed for reproducibility (`SEED`)
### Events of interest (must be clearly stated and motivated)
- [x] Knicks' simulated wins and conference rank vs. actual
- [x] P(Knicks win the title) and how surprising that champion is
- [x] P(each team wins the title), the most likely champions
- [x] P(each playoff seed wins a round / reaches the Finals / wins the title)
- [ ] **Finals matchups.** The assignment suggests events like "Team A and Team B make the Finals and Team A wins". The code doesn't track these yet, so return `fin$win` / `fin$lose` from `simulate_chunk()`.
- [ ] Decide on a final short list (3–5) of events and write a sentence on why each matters
- [ ] Compare `PARAM_UNCERTAINTY = TRUE` vs. `FALSE` as a robustness check
- [ ] A few concrete examples to complement the numbers (e.g. a specific simulated season where the Knicks win)
---
 
## 2. Written report (PDF)
 
Render the report as a PDF from Quarto, or render to HTML and save as PDF.
 
### Executive summary
- [ ] 500 words or fewer
- [ ] Non-technical language: no jargon, code, figures, tables, or charts
- [ ] States the goal, approach, and main conclusions
- [ ] Readable by a front-office executive, coach, player, or fan
### Technical report
- [ ] **Problem statement and background:** why this question is interesting and important
- [ ] **Data and major analysis steps** (data source, cleaning decisions such as the Cup / All-Star / postponed-game fixes)
- [ ] **Model description:** the equation, home-court term, how uncertainty is handled
- [ ] **Main results** in context, supported by figures and tables
- [ ] Code and output tightly integrated with the text (enough that someone else can replicate it)
- [ ] **Limitations** (static ratings, no injuries, random tiebreakers, one home-court constant, etc.)
- [ ] **Concrete next steps** for further development
- [ ] Explicitly state the events of interest, and why
---
 
## 3. Presentation (8–10 minutes, `.mp4`)
 
Record with Zoom. **The speaker's face must be visible alongside the slides.**
 
- [ ] **Background (2–4 slides):** motivate the problem, why it matters
- [ ] **Analysis overview (2–4 slides):** main steps, why each was needed (ideas, not syntax)
- [ ] **Main results (2–3 slides):** a few key points with figures/tables
- [ ] **Conclusion (1 slide):** summary and 1–3 specific future directions
- [ ] Clearly state the events of interest
- [ ] Time a practice run (8–10 min)
- [ ] Record, and check the face and audio
---
 
## 4. Submission
 
File names (replace `00` with your team ID):
 
- [ ] `00_report.pdf`
- [ ] `00_presentation.mp4`
- [ ] `00_code.zip` or `00_code.tar.gz` containing the `.qmd` and any external data
  (data pulled live with `hoopR` doesn't need to be included, but `GAMES_CSV` data would)
- [ ] Sign in to Box with your **Wisconsin NetID** credentials
- [ ] Upload each file through its **separate** submission link (report, presentation, code)
- [ ] Confirm all three uploads went through
---
 
## 5. Peer reviews (due Nov 13, noon)
 
- [ ] Check for your three assigned projects (announced at noon on Nov 6)
- [ ] Complete the Qualtrics survey **three separate times**, once per project
---
 
## Suggested timeline
 
| Date | Goal |
|---|---|
| Tue Oct 27 – Wed Oct 28 | Finish data cleaning, confirm 1,230 games, run the sims on real data |
| Thu Oct 29 – Sat Oct 31 | Add Finals matchups, finalize events of interest, optional covariate model |
| Sun Nov 1 – Mon Nov 2 | Draft the technical report and the executive summary |
| Tue Nov 3 | Build slides and do a practice run |
| Wed Nov 4 | Record the presentation, render the PDF |
| Thu Nov 5 | Final review, zip the code, test uploads |
| **Fri Nov 6, before noon** | **Submit everything** |
 