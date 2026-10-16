# COIL — environmental monitoring dashboard

[Back to profile](../README.md)

**Context:** University of Leeds software engineering team project, with international Collaborative Online International Learning workshops involving South African students.

**Project stack:** Python, Flask, SQLAlchemy, NumPy, pandas, Matplotlib, SVG and pytest.

## Problem

The team developed a water-quality monitoring dashboard that presents environmental readings, historical trends and alert thresholds. Dense time-series charts added display latency and made the amount of rendered data a practical engineering concern.

The coursework uses environmental monitoring data supplied for the project, including synthetic sensor data. This is a university prototype, not a claim of a deployed community sensor network.

## My contribution

I was responsible for displaying data in the dashboard and implementing Largest Triangle Three Buckets (LTTB) downsampling to reduce the work needed to display graphs.

The chart service samples dense series before rendering them with Matplotlib as SVG. The inspected implementation uses a **500-point threshold**, retains the endpoints and selects points based on triangle area to preserve the broad visual shape of a series.

## Why this approach

Uniformly selecting every nth point can miss visually important changes. LTTB prioritises points that contribute to the shape of the chart. It offers a practical balance between the number of plotted points and the usefulness of a trend view.

Downsampling is a display optimisation. Alert logic and analytical calculations should use the underlying data; the displayed subset should not be treated as a replacement for the original readings.

## Evidence and limits

The team archive contains the Flask chart service, LTTB implementation, SVG chart templates and chart tests. My role is stated separately from the team's wider ingestion, storage, filtering and alert work.

No exact speedup or project mark is claimed here: comparable timing measurements and the precise assessment result are still to be confirmed. A useful follow-up is to benchmark the same datasets before and after downsampling and report dataset size, hardware, repetitions and chart time.

The team repository remains private. This write-up summarises my contribution without republishing the team's source or coursework datasets.
