google-map-react を用いた最小構成

```tsx
import React, { Component } from 'react';
import styled from 'styled-components'

import GoogleMapReact from 'google-map-react';

const MapTittle = styled.h1`
  color: #016AC4;
  text-align: center;
`
const Pin = styled.div<{
  lat: number,
  lng: number
}>`
`

const GoogleMapWrapper = styled.div`
  height: 100vh;
  width: 100%;
`

const Map = () => (
  <GoogleMapWrapper>
    <GoogleMapReact
      bootstrapURLKeys={{ key: '' }}
      defaultCenter={{
        lat: 35.681236,
        lng: 139.767125
      }}
      defaultZoom={15}
    >
      <Pin
        lat={35.681236}
        lng={139.767125}
      >
        東京駅
      </Pin>
    </GoogleMapReact>
  </GoogleMapWrapper>
)

export default Map
```
