# Sibiliant-challenge

## The Problem

Given a list of meetings with start and end times, the task is to determine the minimum number of meeting rooms required so that no two meetings overlap in the same room.

## Quick Start

### Prerequisites

- Node.js installed on your system

### Installation

```bash
npm install -g sibilant
```

### Running the Code

sibilant -x -f meeting-room.sibilant

```

That's it! The program will run all test cases and show the results.

## How It Works

The solution uses a "sweep line" algorithm - imagine a vertical line moving from left to right across a timeline:

1. **Create Events**: For each meeting, we create two events:

   - Meeting starts → need +1 room
   - Meeting ends → free -1 room

2. **Sort Timeline**: Put all events in chronological order

3. **Sweep**: Move through time, keeping track of how many rooms we're using. The peak usage is our answer.

**Why this works:** At any point in time, the number of active meetings equals the number of rooms needed at that moment.

## Algorithm Complexity

- **Time**: O(n log n) - mostly due to sorting the events
- **Space**: O(n) - we store events for each meeting

This is optimal since we need to consider the temporal relationships between all meetings.

## Test Cases Included

The solution includes comprehensive tests covering:

- **Basic scenarios**: overlapping, non-overlapping, adjacent meetings
- **Edge cases**: empty input, single meeting, zero-duration meetings
- **Complex patterns**: nested meetings, same start/end times, decimal timestamps
- **Stress tests**: multiple meetings with various overlap patterns

## Expected Output

```

Example meetings: 2
No overlap meetings: 1
All at once: 3
Empty meetings: 0
Single meeting: 1
...

```

## About the Solution

The algorithm handles all edge cases correctly:

- Meetings that start exactly when others end
- Multiple meetings at the same time
- Fractional time values
- Empty or single-meeting inputs
```
