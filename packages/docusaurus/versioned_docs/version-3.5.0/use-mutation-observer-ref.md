---
id: version-3.5.0-use-mutation-observer-ref
title: use-mutation-observer-ref
sidebar_label: use-mutation-observer-ref
original_id: use-mutation-observer-ref
---

# @rooks/use-mutation-observer-ref

### A hook that tracks mutations of an element. It returns a callbackRef.

[![Build Status](https://travis-ci.org/imbhargav5/rooks.svg?branch=master)](https://travis-ci.org/imbhargav5/rooks) ![](https://img.shields.io/npm/v/@rooks/use-mutation-observer-ref/latest.svg) ![](https://img.shields.io/npm/l/@rooks/use-mutation-observer-ref.svg) ![](https://img.shields.io/bundlephobia/min/@rooks/use-mutation-observer-ref.svg) ![](https://img.shields.io/david/imbhargav5/rooks.svg?path=packages%2Fmutation-observer-ref)

<a href="https://spectrum.chat/rooks"><img src="https://withspectrum.github.io/badge/badge.svg" alt="Join the community on Spectrum"/></a>

### Installation

```
npm install --save @rooks/use-mutation-observer-ref
```

### Importing the hook

```javascript
import useMutationObserverRef from "@rooks/use-mutation-observer-ref"
```

### Usage

```jsx
function Demo() {
  const [mutationCount, setMutationCount] = useState(0);
  const incrementMutationCount = () => {
    return setMutationCount(mutationCount + 1);
  };
  const [myRef] = useMutationObserver(myRef, incrementMutationCount);
  const [XOffset, setXOffset] = useState(0);
  const [YOffset, setYOffset] = useState(300);
  return (
    <>
      <div
        style={{
          width: 300,
          background: "lightblue",
          padding: "10px",
          position: "absolute",
          left: XOffset,
          top: YOffset
        }}
        ref={myRef}
      >
        <div
          style={{
            resize: "both",
            overflow: "auto",
            background: "white",
            color: "blue",
            maxWidth: "100%"
          }}
        >
          <p>
            Resize this div as you see fit. To demonstrate that it also updates
            on child dom nodes resize
          </p>
        </div>
        <h2>Bounds</h2>
        <p>
          <button onClick={() => setXOffset(XOffset - 5)}> Move Left </button>
          <button onClick={() => setXOffset(XOffset + 5)}> Move Right </button>
        </p>
        <p>
          <button onClick={() => setYOffset(YOffset - 5)}> Move Up </button>
          <button onClick={() => setYOffset(YOffset + 5)}> Move Down </button>
        </p>
      </div>
      <div style={{ height: 500 }} onClick={incrementMutationCount}>
        <pre>Mutation count {mutationCount}</pre>
      </div>
    </>
  );
}

render(<Demo/>)
```

### Arguments

| Argument | Type     | Description                                                                                       | Default value                                                           |
| -------- | -------- | ------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| callback | function | Function which should be invoked on mutation. It is called with the `mutationList` and `observer` | undefined                                                               |
| config   | object   | Mutation Observer configuration                                                                   | {attributes: true,,characterData: true,,subtree: true,,childList: true} |
### Return value

Returns an array with one element

| Argument | Type      | Description                                |
| -------- | --------- | ------------------------------------------ |
| ref      | React ref | Ref which should be observed for Mutations |



    