<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 1200">
    <!-- Half Adder Circuit -->
    <g transform="translate(50,50)">
        <text x="0" y="30" font-size="16" font-weight="bold">Half Adder Circuit</text>
        
        <!-- Input A -->
        <path d="M50,100 L150,100" stroke="black" fill="none"/>
        <text x="30" y="105">A</text>
        
        <!-- Input B -->
        <path d="M50,200 L150,200" stroke="black" fill="none"/>
        <text x="30" y="205">B</text>
        
        <!-- XOR Gate -->
        <path d="M150,90 Q170,100 150,110 Q200,100 150,90" stroke="black" fill="none"/>
        <text x="160" y="105">XOR</text>
        
        <!-- AND Gate -->
        <path d="M150,190 L180,190 A20,20 0 0,1 180,210 L150,210" stroke="black" fill="none"/>
        <text x="160" y="205">AND</text>
        
        <!-- Outputs -->
        <path d="M200,100 L250,100" stroke="black" fill="none"/>
        <text x="260" y="105">Sum</text>
        
        <path d="M200,200 L250,200" stroke="black" fill="none"/>
        <text x="260" y="205">Carry</text>
    </g>

    <!-- Truth Table -->
    <g transform="translate(400,50)">
        <text x="0" y="30" font-size="16" font-weight="bold">Truth Table</text>
        
        <!-- Headers -->
        <text x="20" y="60">A</text>
        <text x="60" y="60">B</text>
        <text x="100" y="60">Sum</text>
        <text x="160" y="60">Carry</text>
        
        <!-- Lines -->
        <line x1="10" y1="70" x2="200" y2="70" stroke="black"/>
        
        <!-- Values -->
        <text x="20" y="90">0</text>
        <text x="60" y="90">0</text>
        <text x="100" y="90">0</text>
        <text x="160" y="90">0</text>
        
        <text x="20" y="110">0</text>
        <text x="60" y="110">1</text>
        <text x="100" y="110">1</text>
        <text x="160" y="110">0</text>
        
        <text x="20" y="130">1</text>
        <text x="60" y="130">0</text>
        <text x="100" y="130">1</text>
        <text x="160" y="130">0</text>
        
        <text x="20" y="150">1</text>
        <text x="60" y="150">1</text>
        <text x="100" y="150">0</text>
        <text x="160" y="150">1</text>
    </g>

    <!-- Full Adder Circuit -->
    <g transform="translate(50,300)">
        <text x="0" y="30" font-size="16" font-weight="bold">Full Adder Circuit</text>
        
        <!-- Inputs -->
        <path d="M50,100 L150,100" stroke="black" fill="none"/>
        <text x="30" y="105">A</text>
        
        <path d="M50,200 L150,200" stroke="black" fill="none"/>
        <text x="30" y="205">B</text>
        
        <path d="M50,300 L150,300" stroke="black" fill="none"/>
        <text x="30" y="305">Cin</text>
        
        <!-- First XOR Gate -->
        <path d="M150,90 Q170,100 150,110 Q200,100 150,90" stroke="black" fill="none"/>
        <text x="160" y="105">XOR1</text>
        
        <!-- Second XOR Gate -->
        <path d="M250,90 Q270,100 250,110 Q300,100 250,90" stroke="black" fill="none"/>
        <text x="260" y="105">XOR2</text>
        
        <!-- First AND Gate -->
        <path d="M150,190 L180,190 A20,20 0 0,1 180,210 L150,210" stroke="black" fill="none"/>
        <text x="160" y="205">AND1</text>
        
        <!-- Second AND Gate -->
        <path d="M250,190 L280,190 A20,20 0 0,1 280,210 L250,210" stroke="black" fill="none"/>
        <text x="260" y="205">AND2</text>
        
        <!-- OR Gate -->
        <path d="M350,190 Q370,200 350,210 Q400,200 350,190" stroke="black" fill="none"/>
        <text x="360" y="205">OR</text>
        
        <!-- Outputs -->
        <path d="M300,100 L350,100" stroke="black" fill="none"/>
        <text x="360" y="105">Sum</text>
        
        <path d="M400,200 L450,200" stroke="black" fill="none"/>
        <text x="460" y="205">Carry</text>
    </g>

    <!-- K-maps -->
    <g transform="translate(400,300)">
        <text x="0" y="30" font-size="16" font-weight="bold">K-maps</text>
        
        <!-- Sum K-map -->
        <rect x="20" y="60" width="160" height="100" fill="none" stroke="black"/>
        <text x="20" y="50">Sum K-map</text>
        
        <!-- Headers -->
        <text x="60" y="80">B=0</text>
        <text x="120" y="80">B=1</text>
        <text x="0" y="100">A=0</text>
        <text x="0" y="140">A=1</text>
        
        <!-- Values -->
        <text x="70" y="100">0</text>
        <text x="130" y="100">1</text>
        <text x="70" y="140">1</text>
        <text x="130" y="140">0</text>
    </g>

    <!-- SOP Expressions -->
    <g transform="translate(50,600)">
        <text x="0" y="30" font-size="16" font-weight="bold">SOP Expressions</text>
        <text x="20" y="60">Sum = A'B + AB'</text>
        <text x="20" y="90">Carry = AB</text>
    </g>
</svg>