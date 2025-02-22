<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 500">
    <!-- Signal Routing System Definition -->
    <defs>
        <!-- Input Terminal Markers -->
        <marker id="inputDot" viewBox="0 0 10 10" refX="5" refY="5" 
                markerWidth="4" markerHeight="4">
            <circle cx="5" cy="5" r="4" fill="#2c5282"/>
        </marker>
        
        <!-- Junction Indicators -->
        <marker id="junction" viewBox="0 0 10 10" refX="5" refY="5"
                markerWidth="4" markerHeight="4">
            <circle cx="5" cy="5" r="4" fill="#4299e1"/>
        </marker>
    </defs>

    <!-- Main Circuit Frame -->
    <rect x="50" y="50" width="700" height="400" 
          fill="#f7fafc" stroke="#2d3748" stroke-width="2"/>

    <!-- Title and System Description -->
    <text x="60" y="40" font-family="monospace" font-size="20" font-weight="bold"
          fill="#2d3748">Half Adder Signal Routing Diagram</text>

    <!-- Input A Signal Path System -->
    <g transform="translate(100,150)">
        <!-- Input Terminal A -->
        <text x="-20" y="5" font-family="monospace" font-size="16" 
              text-anchor="end" fill="#2c5282">A</text>
        <circle cx="0" cy="0" r="4" fill="#2c5282"/>
        
        <!-- Primary Distribution Path -->
        <path d="M0,0 H60" stroke="#2c5282" stroke-width="3"/>
        
        <!-- Branch Point -->
        <circle cx="60" cy="0" r="4" fill="#4299e1"/>
        
        <!-- XOR Branch -->
        <path d="M60,0 H120" stroke="#2c5282" stroke-width="3"/>
        
        <!-- AND Branch -->
        <path d="M60,0 V100 H120" stroke="#2c5282" stroke-width="3"/>
        
        <!-- Signal Labels -->
        <text x="30" y="-10" font-family="monospace" font-size="12" fill="#4a5568">A to XOR</text>
        <text x="70" y="70" font-family="monospace" font-size="12" fill="#4a5568">A to AND</text>
    </g>

    <!-- Input B Signal Path System -->
    <g transform="translate(100,250)">
        <!-- Input Terminal B -->
        <text x="-20" y="5" font-family="monospace" font-size="16" 
              text-anchor="end" fill="#2c5282">B</text>
        <circle cx="0" cy="0" r="4" fill="#2c5282"/>
        
        <!-- Primary Distribution Path -->
        <path d="M0,0 H60" stroke="#2c5282" stroke-width="3"/>
        
        <!-- Branch Point -->
        <circle cx="60" cy="0" r="4" fill="#4299e1"/>
        
        <!-- XOR Branch -->
        <path d="M60,0 V-70 H120" stroke="#2c5282" stroke-width="3"/>
        
        <!-- AND Branch -->
        <path d="M60,0 H120" stroke="#2c5282" stroke-width="3"/>
        
        <!-- Signal Labels -->
        <text x="70" y="-40" font-family="monospace" font-size="12" fill="#4a5568">B to XOR</text>
        <text x="30" y="-10" font-family="monospace" font-size="12" fill="#4a5568">B to AND</text>
    </g>

    <!-- Logic Gates -->
    <!-- XOR Gate -->
    <g transform="translate(250,150)">
        <path d="M0,-20 C30,-20 30,20 0,20 C50,0 0,-20 0,-20" 
              fill="white" stroke="#2d3748" stroke-width="2"/>
        <text x="15" y="5" font-family="monospace" font-size="14" fill="#2d3748">XOR</text>
        <!-- Output -->
        <path d="M50,0 H100" stroke="#c53030" stroke-width="3"/>
        <text x="110" y="5" font-family="monospace" font-size="14" fill="#2d3748">Sum</text>
    </g>

    <!-- AND Gate -->
    <g transform="translate(250,250)">
        <path d="M0,-20 H30 A20,20 0 0,1 30,20 H0 Z" 
              fill="white" stroke="#2d3748" stroke-width="2"/>
        <text x="5" y="5" font-family="monospace" font-size="14" fill="#2d3748">AND</text>
        <!-- Output -->
        <path d="M50,0 H100" stroke="#c53030" stroke-width="3"/>
        <text x="110" y="5" font-family="monospace" font-size="14" fill="#2d3748">Carry</text>
    </g>

    <!-- Signal Flow Legend -->
    <g transform="translate(500,100)">
        <rect x="0" y="0" width="200" height="120" 
              fill="white" stroke="#2d3748" stroke-width="1"/>
        <text x="10" y="25" font-family="monospace" font-size="14" 
              font-weight="bold" fill="#2d3748">Signal Flow Legend</text>
        
        <!-- Input Signals -->
        <path d="M10,45 H60" stroke="#2c5282" stroke-width="3"/>
        <text x="70" y="50" font-family="monospace" font-size="12" fill="#4a5568">Input Lines</text>
        
        <!-- Branch Points -->
        <circle cx="35" cy="75" r="4" fill="#4299e1"/>
        <text x="70" y="80" font-family="monospace" font-size="12" fill="#4a5568">Branch Points</text>
        
        <!-- Outputs -->
        <path d="M10,95 H60" stroke="#c53030" stroke-width="3"/>
        <text x="70" y="100" font-family="monospace" font-size="12" fill="#4a5568">Output Lines</text>
    </g>
</svg>