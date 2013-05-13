simple one-off script to generate branch/merge SVG diagrams


Example
-------

    branch_diagramm :weeks => 4 do

      branch :number => "1.25", :title => "Produktion"

      branch :number => "1.26", :title => "Entwicklung" do
        starting :from => "1.25", :day => :monday, :week => 2
      end

      branch :number => "2.0", :title => "I-Test"

      branch :number => "2.1", :title => "Entwicklung" do
        starting :from => "2.0", :day => :wednesday, :week => 1
      end

      merge :from => "1.25", :to => "1.26" do
        each :day => :monday
        starting :week => 3
      end

      merge :from => "1.25", :to => "2.0" do
        each :day => :monday
      end

      merge :from => "1.26", :to => "2.1" do
        each :day => :friday
        starting :week => 2
      end

      merge :from => "2.0", :to => "2.1" do
        each :day => :wednesday
        starting :week => 2
      end
    end

This results in

    <svg xmlns="http://www.w3.org/2000/svg" width="736" height="218">
      <defs>
        <marker id="mergearrow"
          viewBox="0 0 20 16" refX="5" refY="8"
          markerUnits="strokeWidth"
          markerWidth="3" markerHeight="2"
          orient="auto">
          <path d="M 0 0 L 0 16 L 20 8 Z" fill="#00f010" />
        </marker>
        <marker id="timearrow"
          viewBox="0 0 20 16" refX="5" refY="8"
          markerUnits="strokeWidth"
          markerWidth="9" markerHeight="9"
          orient="auto">
          <path d="M 0 0 L 0 16 L 20 8 Z" fill="#000000" />
        </marker>
        <style type="text/css">
          .merge {
            stroke: #00f010;
            fill: none;
            stroke-width: 7;
            marker-end: url(#mergearrow);
          }
          .timeline {
            marker-end: url(#timearrow);
          }
          .branchline {
            fill: none;
            stroke-width: 25;
          }
          text {
            font-family: &quot;FreeSans&quot;, sans-serif;
            fill: #000000;
            font-style: normal;
            font-weight: normal;
          }
          text.branchnr, text.branchtitle, text.mergeday {
            font-size: 20px;
          }
          text.day {
            text-anchor: middle;
            font-size: 14;
          }
        </style>
      </defs>
      <g transform="scale(0.7) translate(20,0)">
      <text x="0" y="36.2" class="branchnr">1.25</text>
      <path d="M 62.5 30 L 980 30" stroke="#ffb020" class="branchline" />
      <text x="0" y="96.2" class="branchnr">1.26</text>
      <path d="M 306.0 30 a 14 14 0 0 1 14 14 L 320.0 76 A 14 14 0 0 0 334.0 90 L 980 90" stroke="#4c90ff" class="branchline" />
      <text x="0" y="156.2" class="branchnr">2.0</text>
      <path d="M 62.5 150 L 980 150" stroke="#ffff00" class="branchline" />
      <text x="0" y="216.2" class="branchnr">2.1</text>
      <path d="M 148.857142857143 150 a 14 14 0 0 1 14 14 L 162.857142857143 196 A 14 14 0 0 0 176.857142857143 210 L 980 210" stroke="#4c90ff" class="branchline" />
      <path d="M 526.0 30 a 14 14 0 0 1 14 14 L 540.0 76 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 746.0 30 a 14 14 0 0 1 14 14 L 760.0 76 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 86.0 30 a 14 14 0 0 1 14 14 L 100.0 136 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 306.0 30 a 14 14 0 0 1 14 14 L 320.0 136 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 526.0 30 a 14 14 0 0 1 14 14 L 540.0 136 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 746.0 30 a 14 14 0 0 1 14 14 L 760.0 136 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 431.714285714286 90 a 14 14 0 0 1 14 14 L 445.714285714286 196 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 651.714285714286 90 a 14 14 0 0 1 14 14 L 665.714285714286 196 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 871.714285714286 90 a 14 14 0 0 1 14 14 L 885.714285714286 196 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 368.857142857143 150 a 14 14 0 0 1 14 14 L 382.857142857143 196 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 588.857142857143 150 a 14 14 0 0 1 14 14 L 602.857142857143 196 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <path d="M 808.857142857143 150 a 14 14 0 0 1 14 14 L 822.857142857143 196 a 14 14 0 0 0 14 14 l 4 0" class="merge" />
      <text x="100.0" y="280" class="day">Mo</text>
      <path d="M 100.0 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="131.428571428571" y="280" class="day">Di</text>
      <path d="M 131.428571428571 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="162.857142857143" y="280" class="day">Mi</text>
      <path d="M 162.857142857143 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="194.285714285714" y="280" class="day">Do</text>
      <path d="M 194.285714285714 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="225.714285714286" y="280" class="day">Fr</text>
      <path d="M 225.714285714286 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="257.142857142857" y="280" class="day">Sa</text>
      <path d="M 257.142857142857 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="288.571428571429" y="280" class="day">So</text>
      <path d="M 288.571428571429 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="320.0" y="280" class="day">Mo</text>
      <path d="M 320.0 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="351.428571428571" y="280" class="day">Di</text>
      <path d="M 351.428571428571 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="382.857142857143" y="280" class="day">Mi</text>
      <path d="M 382.857142857143 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="414.285714285714" y="280" class="day">Do</text>
      <path d="M 414.285714285714 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="445.714285714286" y="280" class="day">Fr</text>
      <path d="M 445.714285714286 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="477.142857142857" y="280" class="day">Sa</text>
      <path d="M 477.142857142857 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="508.571428571429" y="280" class="day">So</text>
      <path d="M 508.571428571429 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="540.0" y="280" class="day">Mo</text>
      <path d="M 540.0 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="571.428571428571" y="280" class="day">Di</text>
      <path d="M 571.428571428571 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="602.857142857143" y="280" class="day">Mi</text>
      <path d="M 602.857142857143 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="634.285714285714" y="280" class="day">Do</text>
      <path d="M 634.285714285714 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="665.714285714286" y="280" class="day">Fr</text>
      <path d="M 665.714285714286 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="697.142857142857" y="280" class="day">Sa</text>
      <path d="M 697.142857142857 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="728.571428571429" y="280" class="day">So</text>
      <path d="M 728.571428571429 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="760.0" y="280" class="day">Mo</text>
      <path d="M 760.0 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="791.428571428571" y="280" class="day">Di</text>
      <path d="M 791.428571428571 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="822.857142857143" y="280" class="day">Mi</text>
      <path d="M 822.857142857143 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="854.285714285714" y="280" class="day">Do</text>
      <path d="M 854.285714285714 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="885.714285714286" y="280" class="day">Fr</text>
      <path d="M 885.714285714286 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="917.142857142857" y="280" class="day">Sa</text>
      <path d="M 917.142857142857 257.6 l 0 8.4" stroke="#000000" /> 
      <text x="948.571428571429" y="280" class="day">So</text>
      <path d="M 948.571428571429 257.6 l 0 8.4" stroke="#000000" /> 
      <path d="M 68.5714285714286 261.8 L 980.0 261.8" stroke="#000000" class="timeline" />
     </g>
    </svg>

----

    <svg xmlns="http://www.w3.org/2000/svg" width="414" height="270">
      <defs>
        <marker id="mergearrow"
          viewBox="0 0 20 16" refX="5" refY="8"
          markerUnits="strokeWidth"
          markerWidth="3" markerHeight="2"
          orient="auto">
          <path d="M 0 0 L 0 16 L 20 8 Z" fill="#00f010" />
        </marker>
        <style type="text/css">
          .merge {
            stroke: #00f010;
            fill: none;
            stroke-width: 7;
            marker-end: url(#mergearrow);
          }
          text {
            font-family: &quot;FreeSans&quot;, sans-serif;
            fill: #000000;
            font-style: normal;
            font-weight: normal;
            font-size: 17px;
            text-anchor: middle;
          }
        </style>
      </defs>
      <rect x="50" y="25" width="120" height="55" fill="#ffb020" />
      <text x="110.0" y="50">1.25</text>
      <text x="110.0" y="70">Produktion</text>
      <rect x="274" y="25" width="120" height="55" fill="#4c90ff" />
      <text x="334.0" y="50">1.26</text>
      <text x="334.0" y="70">Entwicklung</text>
      <rect x="50" y="184" width="120" height="55" fill="#ffff00" />
      <text x="110.0" y="209">2.0</text>
      <text x="110.0" y="229">I-Test</text>
      <rect x="274" y="184" width="120" height="55" fill="#4c90ff" />
      <text x="334.0" y="209">2.1</text>
      <text x="334.0" y="229">Entwicklung</text>
      <path d="M 187 52 l 60 0" class="merge" />
     <path d="M 110 97 l 0 60" class="merge" />
     <path d="M 334 97 l 0 60" class="merge" />
      <path d="M 187 211 l 60 0" class="merge" />
    </svg>
