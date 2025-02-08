<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 1400">
    <!-- Section 1: Half Adder Design -->
    <g transform="translate(50,50)">
        <text x="0" y="30" font-family="monospace" font-size="20" font-weight="bold">1. Half Adder Circuit Implementation</text>
        
        <!-- Circuit Frame -->
        <rect x="10" y="50" width="400" height="200" fill="none" stroke="#333" stroke-width="2"/>
        
        <!-- Input A -->
        <path d="M30,100 L130,100" stroke="#2c5282" stroke-width="2"/>
        <text x="20" y="95" font-family="monospace" font-size="16">A</text>
        <circle cx="30" cy="100" r="3" fill="#2c5282"/>
        
        <!-- Input B -->
        <path d="M30,180 L130,180" stroke="#2c5282" stroke-width="2"/>
        <text x="20" y="175" font-family="monospace" font-size="16">B</text>
        <circle cx="30" cy="180" r="3" fill="#2c5282"/>
        
        <!-- XOR Gate -->
        <path d="M130,90 C160,90 160,110 130,110 C180,100 130,90 130,90" 
              fill="none" stroke="#444" stroke-width="2"/>
        <text x="140" y="105" font-family="monospace" font-size="14">XOR</text>
        
        <!-- AND Gate -->
        <path d="M130,170 L160,170 A20,20 0 0,1 160,190 L130,190" 
              fill="none" stroke="#444" stroke-width="2"/>
        <text x="135" y="185" font-family="monospace" font-size="14">AND</text>
        
        <!-- Outputs -->
        <path d="M200,100 L300,100" stroke="#c53030" stroke-width="2"/>
        <text x="310" y="105" font-family="monospace" font-size="16">Sum</text>
        
        <path d="M200,180 L300,180" stroke="#c53030" stroke-width="2"/>
        <text x="310" y="185" font-family="monospace" font-size="16">Carry</text>
    </g>

    <!-- Section 2: Truth Table -->
    <g transform="translate(500,50)">
        <text x="0" y="30" font-family="monospace" font-size="20" font-weight="bold">2. Truth Table Analysis</text>
        
        <!-- Table Frame -->
        <rect x="10" y="50" width="400" height="200" fill="none" stroke="#333" stroke-width="2"/>
        
        <!-- Headers -->
        <text x="40" y="80" font-family="monospace" font-size="16" font-weight="bold">A</text>
        <text x="120" y="80" font-family="monospace" font-size="16" font-weight="bold">B</text>
        <text x="200" y="80" font-family="monospace" font-size="16" font-weight="bold">Sum</text>
        <text x="300" y="80" font-family="monospace" font-size="16" font-weight="bold">Carry</text>
        
        <!-- Separator Line -->
        <line x1="20" y1="90" x2="390" y2="90" stroke="#333" stroke-width="2"/>
        
        <!-- Values -->
        <g font-family="monospace" font-size="16">
            <!-- Row 1 -->
            <text x="40" y="120">0</text>
            <text x="120" y="120">0</text>
            <text x="200" y="120">0</text>
            <text x="300" y="120">0</text>
            
            <!-- Row 2 -->
            <text x="40" y="150">0</text>
            <text x="120" y="150">1</text>
            <text x="200" y="150">1</text>
            <text x="300" y="150">0</text>
            
            <!-- Row 3 -->
            <text x="40" y="180">1</text>
            <text x="120" y="180">0</text>
            <text x="200" y="180">1</text>
            <text x="300" y="180">0</text>
            
            <!-- Row 4 -->
            <text x="40" y="210">1</text>
            <text x="120" y="210">1</text>
            <text x="200" y="210">0</text>
            <text x="300" y="210">1</text>
        </g>
    </g>

    <!-- Section 3: K-Maps -->
    <g transform="translate(50,350)">
        <text x="0" y="30" font-family="monospace" font-size="20" font-weight="bold">3. Karnaugh Maps</text>
        
        <!-- Sum K-map -->
        <g transform="translate(0,50)">
            <text x="0" y="0" font-family="monospace" font-size="16">Sum K-map</text>
            <rect x="50" y="20" width="200" height="100" fill="none" stroke="#333" stroke-width="2"/>
            
            <!-- Grid -->
            <line x1="150" y1="20" x2="150" y2="120" stroke="#333" stroke-width="1"/>
            <line x1="50" y1="70" x2="250" y2="70" stroke="#333" stroke-width="1"/>
            
            <!-- Labels -->
            <text x="100" y="15" font-family="monospace" font-size="14">B=0</text>
            <text x="200" y="15" font-family="monospace" font-size="14">B=1</text>
            <text x="30" y="50" font-family="monospace" font-size="14">A=0</text>
            <text x="30" y="100" font-family="monospace" font-size="14">A=1</text>
            
            <!-- Values -->
            <text x="100" y="50" font-family="monospace" font-size="16">0</text>
            <text x="200" y="50" font-family="monospace" font-size="16">1</text>
            <text x="100" y="100" font-family="monospace" font-size="16">1</text>
            <text x="200" y="100" font-family="monospace" font-size="16">0</text>
        </g>

        <!-- Carry K-map -->
        <g transform="translate(300,50)">
            <text x="0" y="0" font-family="monospace" font-size="16">Carry K-map</text>
            <rect x="50" y="20" width="200" height="100" fill="none" stroke="#333" stroke-width="2"/>
            
            <!-- Grid -->
            <line x1="150" y1="20" x2="150" y2="120" stroke="#333" stroke-width="1"/>
            <line x1="50" y1="70" x2="250" y2="70" stroke="#333" stroke-width="1"/>
            
            <!-- Labels -->
            <text x="100" y="15" font-family="monospace" font-size="14">B=0</text>
            <text x="200" y="15" font-family="monospace" font-size="14">B=1</text>
            <text x="30" y="50" font-family="monospace" font-size="14">A=0</text>
            <text x="30" y="100" font-family="monospace" font-size="14">A=1</text>
            
            <!-- Values -->
            <text x="100" y="50" font-family="monospace" font-size="16">0</text>
            <text x="200" y="50" font-family="monospace" font-size="16">0</text>
            <text x="100" y="100" font-family="monospace" font-size="16">0</text>
            <text x="200" y="100" font-family="monospace" font-size="16">1</text>
        </g>
    </g>

    <!-- Section 4: Full Adder Implementation -->
    <g transform="translate(50,600)">
        <text x="0" y="30" font-family="monospace" font-size="20" font-weight="bold">4. Full Adder Circuit Implementation</text>
        
        <!-- Circuit Frame -->
        <rect x="10" y="50" width="600" height="300" fill="none" stroke="#333" stroke-width="2"/>
        
        <!-- Inputs -->
        <g stroke="#2c5282" stroke-width="2">
            <!-- A Input -->
            <path d="M30,100 L130,100"/>
            <text x="20" y="95" font-family="monospace" font-size="16">A</text>
            <circle cx="30" cy="100" r="3" fill="#2c5282"/>
            
            <!-- B Input -->
            <path d="M30,180 L130,180"/>
            <text x="20" y="175" font-family="monospace" font-size="16">B</text>
            <circle cx="30" cy="180" r="3" fill="#2c5282"/>
            
            <!-- Cin Input -->
            <path d="M30,260 L130,260"/>
            <text x="20" y="255" font-family="monospace" font-size="16">Cin</text>
            <circle cx="30" cy="260" r="3" fill="#2c5282"/>
        </g>

        <!-- Gates -->
        <!-- First Stage XOR -->
        <path d="M130,90 C160,90 160,110 130,110 C180,100 130,90 130,90" 
              fill="none" stroke="#444" stroke-width="2"/>
        <text x="140" y="105" font-family="monospace" font-size="14">XOR1</text>

        <!-- Second Stage XOR -->
        <path d="M250,90 C280,90 280,110 250,110 C300,100 250,90 250,90" 
              fill="none" stroke="#444" stroke-width="2"/>
        <text x="260" y="105" font-family="monospace" font-size="14">XOR2</text>

        <!-- AND Gates -->
        <path d="M130,170 L160,170 A20,20 0 0,1 160,190 L130,190" 
              fill="none" stroke="#444" stroke-width="2"/>
        <text x="135" y="185" font-family="monospace" font-size="14">AND1</text>

        <path d="M250,170 L280,170 A20,20 0 0,1 280,190 L250,190" 
              fill="none" stroke="#444" stroke-width="2"/>
        <text x="255" y="185" font-family="monospace" font-size="14">AND2</text>

        <!-- OR Gate -->
        <path d="M370,170 C400,170 400,190 370,190 C420,180 370,170 370,170" 
              fill="none" stroke="#444" stroke-width="2"/>
        <text x="385" y="185" font-family="monospace" font-size="14">OR</text>

        <!-- Outputs -->
        <g stroke="#c53030" stroke-width="2">
            <path d="M320,100 L500,100"/>
            <text x="510" y="105" font-family="monospace" font-size="16">Sum</text>
            
            <path d="M440,180 L500,180"/>
            <text x="510" y="185" font-family="monospace" font-size="16">Carry_out</text>
        </g>
    </g>

    <!-- Section 5: SOP Expressions -->
    <g transform="translate(50,1000)">
        <text x="0" y="30" font-family="monospace" font-size="20" font-weight="bold">5. Boolean Expressions (SOP)</text>
        
        <rect x="10" y="50" width="600" height="150" fill="none" stroke="#333" stroke-width="2"/>
        
        <!-- Half Adder Expressions -->
        <text x="30" y="80" font-family="monospace" font-size="16" font-weight="bold">Half Adder:</text>
        <text x="50" y="110" font-family="monospace" font-size="16">Sum = A'B + AB'</text>
        <text x="50" y="140" font-family="monospace" font-size="16">Carry = AB</text>
        
        <!-- Full Adder Expressions -->
        <text x="30" y="170" font-family="monospace" font-size="16" font-weight="bold">Full Adder:</text>
        <text x="50" y="180" font-family="monospace" font-size="16">Sum = A ⊕ B ⊕ Cin</text>
        <text x="50" y="200" font-family="monospace" font-size="16">Carry_out = AB + (A ⊕ B)Cin</text>
    </g>
</svg>