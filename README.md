# siemens-rapidminer-slc-visualizing-antenna-planar-near-field-measurements-using-proc-python
Siemens RapidMiner SLC visualizing antenna planar near-field measurements using proc python
    %let pgm=siemens-rapidminer-slc-visualizing-antenna-planar-near-field-measurements-using-proc-python;

    %stop_submission;

    Siemens RapidMiner SLC visualizing antenna planar near-field measurements using proc python

    Too long to post here: see
    https://github.com/rogerjdeangelis/siemens-rapidminer-slc-visualizing-antenna-planar-near-field-measurements-using-proc-python

    CONTENTS
      1 python near-field model with plots
      2 slc contour plots

    NOTE: this solution uses miniconda python, because the pyanten packages is only available in anaconda or miniconda.

    Related forum post
    https://community.altair.com/discussion/66907/how-can-i-use-rapidminer-for-antenna-measurements?utm_source=community-search&utm_medium=organic-search&utm_term=anten

    Related repo
    https://github.com/rogerjdeangelis/utl-altair-slc-simulating-three-antennae-systems-analyze-co-site-interference-using-s-parameters

    Python is a top choice for antenna measurements due to its extensive, open-source ecosystem for scientific computing, data analysis, and automation.

    Key Capabilities & Libraries
    Data Acquisition & Automation: Python can control measurement equipment (like spectrum analyzers) directly.
    For example, the pyvisa library can communicate with instruments over standard interfaces (GPIB, USB, Ethernet).
    Projects like the Antenna Radiation Mapper and the SIGLENT SSA5085A pattern analyzer show how Python can automate rotation and data sampling.

    Data Processing & Analysis: Libraries like numpy and scipy provide the mathematical foundation for
    processing raw data, performing near-field to far-field (NF-FF) transformations, and calculating key parameters.

    Specialized Toolkits: Several open-source Python toolkits are available:

    A AAFIYA: A modular toolkit for automating antenna characterization using both measurement and simulation data.
    B PyAnten: An antenna toolkit with modules for near-field measurements.
    C Perform: A package containing procedures for measuring parameters like gain and beam shape.
    D pynsi: A module for automating the professional NSI2000 Antenna Measurement Software.

    The example below demonstrates a typical workflow:

    A Plan the measurement: Use PyAnten to calculate the required sampling grid for a planar near-field scan.
    B Simulate data: Generate synthetic near-field data (since we can't acquire it directly in a standalone script).
    C Visualize: Plot the near-field magnitude and phase using matplotlib.

    /*           _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| `_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    */
                                     MAGNITUDE
                                     ---------
                  Plot of y_mm*x_mm=quintile
                  Symbol quintile
                                       X_MM
            -180     -120      -60       0       60       120      180
             -+--------+--------+--------+--------+--------+--------+-
        y_mm |                                                       |
             | QUINTILES (20% PTILES)       MAGNITUDE(WAVE AMPLITUDE)|
             | Plot of y_mm*x_mm=quintile   QUINTILES QUINTILE_RANGE |
             | Symbol quintile              -----------------------  |
             |                                     0  0.01 <= 0.18   |
             |                                     1  0.19 <= 0.35   |
             |                                     2  0.38 <= 0.55   |
             |                                     3  0.55 <= 0.74   |
             |                                     4  0.79 <= 1.00   |
        Y_MM |                                                       | Y_MM
             |                    0 0 0 0 0 0 0                      |
         120 +            0 0 1 1 1 1 2 2 2 1 1 1 1 0 0              +  120
             |          0 0 1 1 2 2 2 2 2 2 2 2 2 1 1 0 0            |
             |        0 1 1 2 2 3 3 3 3 3 3 3 3 3 2 2 1 1 0          |
             |        0 1 2 2 3 3 3 4 4 4 4 4 3 3 3 2 2 1 0          |
             |      0 0 1 2 3 3 3 4 4 4 4 4 4 4 3 3 3 2 1 0 0        |
          20 +      0 1 2 2 3 3 4 4 4 4 4 4 4 4 4 3 3 2 2 1 0        +   20
             |      0 1 2 2 3 3 4 4 4 4 4 4 4 4 4 3 3 2 2 1 0        |
             |      0 1 1 2 3 3 4 4 4 4 4 4 4 4 4 3 3 2 1 1 0        |
             |      0 0 1 2 3 3 3 4 4 4 4 4 4 4 3 3 2 2 1 0 0        |
             |        0 1 1 2 2 3 3 3 3 3 3 3 3 3 2 2 1 1 0          |
         -80 +          0 1 1 2 2 3 3 3 3 3 3 3 2 2 1 1 0            +  -80
             |          0 0 1 1 2 2 2 2 2 2 2 2 2 1 1 0 0            |
             |            0 0 0 0 0 1 1 1 1 1 0 0 0 0 0              |
             |                    0 0 0 0 0 0 0                      |
             |                                                       |
        -180 +                                                       + -180
             -+--------+--------+--------+--------+--------+--------+-
            -180     -120      -60       0       60       120      180
                                       X_MM
                                            m
                                    -----
                                    PHASE
                                    -----
              Plot of Y_MM*X_MM.  Symbol is value of DEGREES.

                                      X_MM
           -180     -120      -60       0       60       120      180
           --+--------+--------+--------+--------+--------+--------+--
        MM |  PHASE OF WAVE FORM       QUINTILE  DEGREES _RANGE      |
           |                           ----------------------------- |
           |                              0      -175.04 <= -126.62  |
           |                              1      -116.69 <= -68.27   |
           |                              2      -58.35 <= 58.35     |
           |                              3      68.27 <= 116.69     |
           |                              4      126.62 <= 175.04    |
        MM |                                                         | Y_MM
           |                                                         |
        40 +                      1 2 2   2 2 3                      +  140
        26 +                  0 1 1 2 2   2 2 3 3  4                 +  126
        12 +             4 0  0 1 1 2 2   2 2 3 3  4 4 0             +  112
        98 +           4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0           +   98
        84 +           4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0           +   84
        70 +         3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1         +   70
        56 +         3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1         +   56
        42 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +   42
        28 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +   28
        14 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +   14
         0 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +    0
        14 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +  -14
        28 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +  -28
        42 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +  -42
        56 +         3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1         +  -56
        70 +         3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1         +  -70
        84 +           4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0           +  -84
        98 +           4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0           +  -98
        12 +             4 0  0 1 1 2 2   2 2 3 3  4 4 0             +  112
        26 +                  0 1 1 2 2   2 2 3 3  4                 +  126
        40 +                      1 2 2   2 2 3                      +  140
           |                                                         |
           --+--------+--------+--------+--------+--------+--------+--
           -180     -120      -60       0       60       120      180
                                      X_MM

    /*               _   _                                             __ _      _     _
    / |  _ __  _   _| |_| |__   ___  _ __    _ __   ___  __ _ _ __    / _(_) ___| | __| |
    | | | `_ \| | | | __| `_ \ / _ \| `_ \  | `_ \ / _ \/ _` | `__|__| |_| |/ _ \ |/ _` |
    | | | |_) | |_| | |_| | | | (_) | | | | | | | |  __/ (_| | | |___|  _| |  __/ | (_| |
    |_| | .__/ \__, |\__|_| |_|\___/|_| |_| |_| |_|\___|\__,_|_|     |_| |_|\___|_|\__,_|
        |_|    |___/
    */

    libname workx sas7bdat "d:/wpswrkx"; /*--- put this in your autoexec ---*/

    %utlfkil(d:/png/anten.png);
    %utlfkil(d:/csv/nearfield_data.csv);

    proc datasets lib=workx kill;
    run;

    options validvarname=v7;
    options set=PYTHONHOME "D:\miniconda";  /*--- MINICONDA ---*/
    proc python;
    submit;
    import matplotlib.pyplot as plt
    import os
    import numpy as np
    import pandas as pd   # <-- ADD THIS

    # Import PyAnten modules for planar near-field measurement planning
    from pyanten.Measurement.NearField.Planar import samplingParameters

    # --- 1. Plan the Planar Near-Field Measurement ---
    frequency = 10e9
    scan_length = 0.5
    Lm, Lp, N, delta_mm = samplingParameters(frequency, scan_length)

    print(f"Planar Near-Field Measurement Plan:")
    print(f"  Frequency:        {frequency/1e9:.1f} GHz")
    print(f"  Scan length:      {scan_length*1000:.0f} mm")
    print(f"  Sample spacing:   {delta_mm} mm")
    print(f"  Number of samples: {N}")
    print(f"  Scan range:        {Lm*1000:.1f} mm to {Lp*1000:.1f} mm")

    # Create spatial grid
    x_positions = np.linspace(Lm, Lp, N)
    y_positions = np.linspace(Lm, Lp, N)
    X, Y = np.meshgrid(x_positions, y_positions)

    # --- 2. Simulate Near-Field Data ---
    aperture_center_x, aperture_center_y = 0.0, 0.0
    aperture_radius = 0.15
    r = np.sqrt((X - aperture_center_x)**2 + (Y - aperture_center_y)**2)

    magnitude = np.cos((r / aperture_radius) * (np.pi / 2))
    magnitude[r > aperture_radius] = 0

    k = 2 * np.pi / (3e8 / frequency)
    theta_steer = 10 * np.pi / 180
    phase = k * X * np.sin(theta_steer)

    near_field_complex = magnitude * np.exp(1j * phase)

    # --- 3. Build a Pandas DataFrame with all data ---
    # Flatten the 2D arrays
    x_flat = X.flatten() * 1000          # convert to mm
    y_flat = Y.flatten() * 1000
    mag_flat = np.abs(near_field_complex).flatten()
    phase_flat = np.angle(near_field_complex, deg=True).flatten()

    df = pd.DataFrame({
        'x_mm': x_flat,
        'y_mm': y_flat,
        'magnitude': mag_flat,
        'phase_deg': phase_flat
    })

    # Print summary
    print("\nDataFrame info:")
    print(df.info())
    print("\nFirst 5 rows:")
    print(df.head())

    # --- 4. (Optional) Save DataFrame to CSV ---
    output_dir = r'd:/csv'
    output_csv = os.path.join(output_dir, 'nearfield_data.csv')
    os.makedirs(output_dir, exist_ok=True)
    df.to_csv(output_csv, index=False)
    print(f"\nDataFrame saved to: {output_csv}")

    # --- 5. Visualize (unchanged, except figure size reduced) ---
    fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(6, 2.5))

    im1 = ax1.imshow(np.abs(near_field_complex),
                     extent=[Lm*1000, Lp*1000, Lm*1000, Lp*1000],
                     origin='lower', cmap='viridis')
    ax1.set_title('Near-Field Magnitude (Linear)')
    ax1.set_xlabel('x (mm)')
    ax1.set_ylabel('y (mm)')
    plt.colorbar(im1, ax=ax1)

    im2 = ax2.imshow(np.angle(near_field_complex, deg=True),
                     extent=[Lm*1000, Lp*1000, Lm*1000, Lp*1000],
                     origin='lower', cmap='twilight')
    ax2.set_title('Near-Field Phase (Degrees)')
    ax2.set_xlabel('x (mm)')
    ax2.set_ylabel('y (mm)')
    plt.colorbar(im2, ax=ax2)

    plt.tight_layout()

    # Save figure
    output_dir = r'd:/png'
    output_file = os.path.join(output_dir, 'anten.png')
    plt.savefig(output_file, dpi=300, bbox_inches='tight')
    print(f"\nGraph saved to: {output_file}")

    plt.close(fig)
    endsubmit;
    import data=workx.anten python=df;
    run;

    proc print data=workx.anten(Obs=10) width=min;
    run;

    /**************************************************************************************************************************/
    /* Planar Near-Field Measurement Plan:                                                                                    */
    /*                                                                                                                        */
    /*    Frequency:        10.0 GHz                                                                                          */
    /*    Scan length:      500 mm                                                                                            */
    /*    Sample spacing:   14 mm                                                                                             */
    /*    Number of samples: 37                                                                                               */
    /*    Scan range:        -252.0 mm to 252.0 mm                                                                            */
    /*                                                                                                                        */
    /*                                                                                                                        */
    /*  DataFrame info:                                                                                                       */
    /*                                                                                                                        */
    /*  <class 'pandas.core.frame.DataFrame'>                                                                                 */
    /*  RangeIndex: 1369 entries, 0 to 1368                                                                                   */
    /*  Data columns (total 4 columns):                                                                                       */
    /*   #   Column     Non-Null Count  Dtype                                                                                 */
    /*  ---  ------     --------------  -----                                                                                 */
    /*   0   x_mm       1369 non-null   float64                                                                               */
    /*   1   y_mm       1369 non-null   float64                                                                               */
    /*   2   magnitude  1369 non-null   float64                                                                               */
    /*   3   phase_deg  1369 non-null   float64                                                                               */
    /*  dtypes: float64(4)                                                                                                    */
    /*  memory usage: 42.9 KB                                                                                                 */
    /*  None                                                                                                                  */
    /*                                                                                                                        */
    /**************************************************************************************************************************/
    /* d:/png/anten.png                                                                                                       */
    /*                                                                                                                        */
    /**************************************************************************************************************************/
    /*   WORKX.ANTEN total obs=1,369                                                                                          */
    /*                                       phase_                                                                           */
    /*    Obs    x_mm    y_mm    magnitude      deg                                                                           */
    /*                                                                                                                        */
    /*      1    -252    -252        0            0                                                                           */
    /*      2    -238    -252        0            0                                                                           */
    /*      3    -224    -252        0            0                                                                           */
    /*      4    -210    -252        0            0                                                                           */
    /*      5    -196    -252        0            0                                                                           */
    /*   ...                                                                                                                  */
    /*   1365     196     252        0            0                                                                           */
    /*   1366     210     252        0            0                                                                           */
    /*   1367     224     252        0          180                                                                           */
    /*   1368     238     252        0          180                                                                           */
    /*   1369     252     252        0          180                                                                           */
    /*                                                                                                                        */
    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*  The MEANS Procedure workx.anten                                     Lower            Upper                            */
    /*  Variable     Label           N       Sum        Mean    Minimum     Quartile Median  Quartile   Maximum  Std Dev      */
    /*  ---------------------------------------------------------------------------------------------------------------       */
    /*  x_mm         x_mm         1369         0           0   -252.00  -126.00        0     126.00     252.00    149.53      */
    /*  y_mm         y_mm         1369         0           0   -252.00  -126.00        0     126.00     252.00    149.53      */
    /*  magnitude    magnitude    1369  166.9003   0.1219140         0        0        0       0.04       1.00      0.25      */
    /*  phase_deg    phase_deg    1369  42300.00  30.8984660   -175.03        0        0      87.51     180.00     88.66      */
    /*                                                                                                                        */
    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* d:/csv/nearfield_data.csv                                                                                              */
    /*                                                                                                                        */
    /* x_mm,y_mm,magnitude,phase_deg                                                                                          */
    /* -252.0,-252.0,0.0,-0.0                                                                                                 */
    /* -238.0,-252.0,0.0,-0.0                                                                                                 */
    /* -224.0,-252.0,0.0,-0.0                                                                                                 */
    /* -210.0,-252.0,0.0,0.0                                                                                                  */
    /* ...                                                                                                                    */
    /* 196.0,252.0,0.0,0.0                                                                                                    */
    /* 210.00000000000003,252.0,0.0,0.0                                                                                       */
    /* 224.00000000000003,252.0,0.0,180.0                                                                                     */
    /* 238.0,252.0,0.0,180.0                                                                                                  */
    /* 252.0,252.0,0.0,180.0                                                                                                  */
    /**************************************************************************************************************************/

    /*
    | | ___   __ _
    | |/ _ \ / _` |
    | | (_) | (_| |
    |_|\___/ \__, |
             |___/
    */

    1                                          Altair SLC          11:10 Tuesday, July 28, 2026

    NOTE: Copyright 2002-2025 World Programming, an Altair Company
    NOTE: Altair SLC 2026 (05.26.01.00.000758)
          Licensed to Roger DeAngelis
    NOTE: This session is executing on the X64_WIN11PRO platform and is running in 64 bit mode

    NOTE: AUTOEXEC processing beginning; file is C:\wpsoto\autoexec.sas

    NOTE: AUTOEXEC processing completed

    1         libname workx sas7bdat "d:/wpswrkx"; /*--- put this in your autoexec ---*/
    NOTE: Library workx assigned as follows:
          Engine:        SAS7BDAT
          Physical Name: d:\wpswrkx

    2
    3         %utlfkil(d:/png/anten.png);
    4         %utlfkil(d:/csv/nearfield_data.csv);

    Altair SLC

    The DATASETS Procedure


    5
    6         proc datasets lib=workx kill;
    7         run;
    NOTE: Deleting WORKX.anten (type=DATA)

    8
    9         options validvarname=v7;
    10        options set=PYTHONHOME "D:\miniconda";
    NOTE: Procedure datasets step took :
          real time : 0.113
          cpu time  : 0.078

    10      !                                         /*--- MINICONDA ---*/
    11        proc python;
    12        submit;
    13        import matplotlib.pyplot as plt
    14        import os
    15        import numpy as np
    16        import pandas as pd   # <-- ADD THIS
    17
    18        # Import PyAnten modules for planar near-field measurement planning
    19        from pyanten.Measurement.NearField.Planar import samplingParameters
    20
    21        # --- 1. Plan the Planar Near-Field Measurement ---
    22        frequency = 10e9
    23        scan_length = 0.5
    24        Lm, Lp, N, delta_mm = samplingParameters(frequency, scan_length)
    25
    26        print(f"Planar Near-Field Measurement Plan:")
    27        print(f"  Frequency:        {frequency/1e9:.1f} GHz")
    28        print(f"  Scan length:      {scan_length*1000:.0f} mm")
    29        print(f"  Sample spacing:   {delta_mm} mm")
    30        print(f"  Number of samples: {N}")
    31        print(f"  Scan range:        {Lm*1000:.1f} mm to {Lp*1000:.1f} mm")
    32
    33        # Create spatial grid
    34        x_positions = np.linspace(Lm, Lp, N)
    35        y_positions = np.linspace(Lm, Lp, N)
    36        X, Y = np.meshgrid(x_positions, y_positions)
    37
    38        # --- 2. Simulate Near-Field Data ---
    39        aperture_center_x, aperture_center_y = 0.0, 0.0
    40        aperture_radius = 0.15
    41        r = np.sqrt((X - aperture_center_x)**2 + (Y - aperture_center_y)**2)
    42
    43        magnitude = np.cos((r / aperture_radius) * (np.pi / 2))
    44        magnitude[r > aperture_radius] = 0
    45
    46        k = 2 * np.pi / (3e8 / frequency)
    47        theta_steer = 10 * np.pi / 180
    48        phase = k * X * np.sin(theta_steer)
    49
    50        near_field_complex = magnitude * np.exp(1j * phase)
    51
    52        # --- 3. Build a Pandas DataFrame with all data ---
    53        # Flatten the 2D arrays
    54        x_flat = X.flatten() * 1000          # convert to mm
    55        y_flat = Y.flatten() * 1000
    56        mag_flat = np.abs(near_field_complex).flatten()
    57        phase_flat = np.angle(near_field_complex, deg=True).flatten()
    58
    59        df = pd.DataFrame({
    60            'x_mm': x_flat,
    61            'y_mm': y_flat,
    62            'magnitude': mag_flat,
    63            'phase_deg': phase_flat
    64        })
    65
    66        # Print summary
    67        print("\nDataFrame info:")
    68        print(df.info())
    69        print("\nFirst 5 rows:")
    70        print(df.head())
    71
    72        # --- 4. (Optional) Save DataFrame to CSV ---
    73        output_dir = r'd:/csv'
    74        output_csv = os.path.join(output_dir, 'nearfield_data.csv')
    75        os.makedirs(output_dir, exist_ok=True)
    76        df.to_csv(output_csv, index=False)
    77        print(f"\nDataFrame saved to: {output_csv}")
    78
    79        # --- 5. Visualize (unchanged, except figure size reduced) ---
    80        fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(6, 2.5))
    81
    82        im1 = ax1.imshow(np.abs(near_field_complex),
    83                         extent=[Lm*1000, Lp*1000, Lm*1000, Lp*1000],
    84                         origin='lower', cmap='viridis')
    85        ax1.set_title('Near-Field Magnitude (Linear)')
    86        ax1.set_xlabel('x (mm)')
    87        ax1.set_ylabel('y (mm)')
    88        plt.colorbar(im1, ax=ax1)
    89
    90        im2 = ax2.imshow(np.angle(near_field_complex, deg=True),
    91                         extent=[Lm*1000, Lp*1000, Lm*1000, Lp*1000],
    92                         origin='lower', cmap='twilight')
    93        ax2.set_title('Near-Field Phase (Degrees)')
    94        ax2.set_xlabel('x (mm)')
    95        ax2.set_ylabel('y (mm)')
    96        plt.colorbar(im2, ax=ax2)
    97
    98        plt.tight_layout()
    99
    100       # Save figure
    101       output_dir = r'd:/png'
    102       output_file = os.path.join(output_dir, 'anten.png')
    103       plt.savefig(output_file, dpi=300, bbox_inches='tight')
    104       print(f"\nGraph saved to: {output_file}")
    105
    106       plt.close(fig)
    107       endsubmit;

    NOTE: Submitting statements to Python:


    108       import data=workx.anten python=df;
    NOTE: Creating data set 'WORKX.anten' from Python data frame 'df'
    NOTE: Data set "WORKX.anten" has 1369 observation(s) and 4 variable(s)

    109       run;
    NOTE: Procedure python step took :
          real time : 27.835
          cpu time  : 0.078

    110
    111       proc print data=workx.anten(Obs=10) width=min;
    112       run;
    NOTE: 10 observations were read from "WORKX.anten"
    NOTE: Procedure print step took :
          real time : 0.016
          cpu time  : 0.015

    NOTE: Submitted statements took :
          real time : 29.368
          cpu time  : 0.421

    /*___        _                        _                          _       _
    |___ \   ___| | ___    ___ ___  _ __ | |_ ___  _   _ _ __  _ __ | | ___ | |_ ___
      __) | / __| |/ __|  / __/ _ \| `_ \| __/ _ \| | | | `__|| `_ \| |/ _ \| __/ __|
     / __/  \__ \ | (__  | (_| (_) | | | | || (_) | |_| | |   | |_) | | (_) | |_\__ \
    |_____| |___/_|\___|  \___\___/|_| |_|\__\___/ \__,_|_|   | .__/|_|\___/ \__|___/
                                                              |_|
    */

    /*--- COMPUTE THE QUINTILES FOR BOTH MAGNITUDE(WAVE AMPLITUDE) AND PHASE_DEG(WAVE FORM) ---*/

    proc rank data=workx.anten(where=(magnitude>0 and phase_deg not in (0,180)))
              out=workx.quintiles
              groups=5;
        var magnitude phase_deg;
        ranks quintile degrees ;
    run;

    /**************************************************************************************************************************/
    /*   WORKX.QUINTILES total obs=336       PHASE_     QUINTILE   QUINTILES                                                  */
    /*  Obs    X_MM    Y_MM    MAGNITUDE       DEG      MAGNITUDE  DEGREES                                                    */
    /*                                                                                                                        */
    /*    1     -42    -140     0.04016      -87.519        0          1                                                      */
    /*    2     -28    -140     0.07561      -58.346        0          2                                                      */
    /*    3     -14    -140     0.09725      -29.173        0          2                                                      */
    /*    4      14    -140     0.09725       29.173        0          2                                                      */
    /*    5      28    -140     0.07561       58.346        0          2                                                      */
    /*   ...                                                                                                                  */
    /*  332     -28     140     0.07561      -58.346        0          2                                                      */
    /*  333     -14     140     0.09725      -29.173        0          2                                                      */
    /*  334      14     140     0.09725       29.173        0          2                                                      */
    /*  335      28     140     0.07561       58.346        0          2                                                      */
    /*  336      42     140     0.04016       87.519        0          3                                                      */
    /**************************************************************************************************************************/

    /*--- CREATE THE LEGENDS ---*/

    options nolabel;
    proc sql;
      select
        'magnitude' as group
        ,quintile
        ,catx(' ',put(min(magnitude),6.2),'<=',put(max(magnitude),6.2)) as QUINTILE_RANGE
      from
         workx.quintiles
      group
         by quintile
      union
         corr
      select
        'degrees' as group
        ,degrees as quintile
        ,catx(' ',put(min(phase_deg),7.2),'<=',put(max(phase_deg),7.2)) as QUINTILE_RANGE
      from
         workx.quintiles
      group
         by degrees
    ;quit;

    /**************************************************************************************************************************/
    /* GROUP      QUINTILE  QUINTILE_RANGE                                                                                    */
    /* -------------------------------------------                                                                            */
    /* DEGREES       0      -175.04 <= -126.62                                                                                */
    /* DEGREES       1      -116.69 <= -68.27                                                                                 */
    /* DEGREES       2      -58.35 <= 58.35                                                                                   */
    /* DEGREES       3      68.27 <= 116.69                                                                                   */
    /* DEGREES       4      126.62 <= 175.04                                                                                  */
    /*                                                                                                                        */
    /* MAGNITUDE     0      0.01 <= 0.18                                                                                      */
    /* MAGNITUDE     1      0.18 <= 0.32                                                                                      */
    /* MAGNITUDE     2      0.35 <= 0.51                                                                                      */
    /* MAGNITUDE     3      0.52 <= 0.74                                                                                      */
    /* MAGNITUDE     4      0.74 <= 0.99                                                                                      */
    /**************************************************************************************************************************/

    /*--- PLOT  ---*/

    options ls=64  ps=44;
    proc plot data=workx.quintiles;
     plot y_mm*x_mm=quintile/box
       haxis=-180 to 180 by 60;
    run;

    proc plot data=workx.quintiles;
     plot y_mm*x_mm=degrees/box
       haxis=-180 to 180 by 60;
    run;
    options ls=255 ps=255;


    /**************************************************************************************************************************/
    /*                                     ---------                                                                          */
    /*                                     MAGNITUDE                                                                          */
    /*                                     ---------                                                                          */
    /*                  Plot of y_mm*x_mm=quintile                                                                            */
    /*                  Symbol quintile                                                                                       */
    /*                                       X_MM                                                                             */
    /*            -180     -120      -60       0       60       120      180                                                  */
    /*             -+--------+--------+--------+--------+--------+--------+-                                                  */
    /*        y_mm |                                                       |                                                  */
    /*             | QUINTILES (20% PTILES)       MAGNITUDE(WAVE AMPLITUDE)|                                                  */
    /*             | Plot of y_mm*x_mm=quintile   QUINTILE  QUINTILE_RANGE |                                                  */
    /*             | Symbol quintile              -----------------------  |                                                  */
    /*             |                                     0  0.01 <= 0.18   |                                                  */
    /*             |                                     1  0.19 <= 0.35   |                                                  */
    /*             |                                     2  0.38 <= 0.55   |                                                  */
    /*             |                                     3  0.55 <= 0.74   |                                                  */
    /*             |                                     4  0.79 <= 1.00   |                                                  */
    /*        Y_MM |                                                       | Y_MM                                             */
    /*             |                    0 0 0 0 0 0 0                      |                                                  */
    /*         120 +            0 0 1 1 1 1 2 2 2 1 1 1 1 0 0              +  120                                             */
    /*             |          0 0 1 1 2 2 2 2 2 2 2 2 2 1 1 0 0            |                                                  */
    /*             |        0 1 1 2 2 3 3 3 3 3 3 3 3 3 2 2 1 1 0          |                                                  */
    /*             |        0 1 2 2 3 3 3 4 4 4 4 4 3 3 3 2 2 1 0          |                                                  */
    /*             |      0 0 1 2 3 3 3 4 4 4 4 4 4 4 3 3 3 2 1 0 0        |                                                  */
    /*          20 +      0 1 2 2 3 3 4 4 4 4 4 4 4 4 4 3 3 2 2 1 0        +   20                                             */
    /*             |      0 1 2 2 3 3 4 4 4 4 4 4 4 4 4 3 3 2 2 1 0        |                                                  */
    /*             |      0 1 1 2 3 3 4 4 4 4 4 4 4 4 4 3 3 2 1 1 0        |                                                  */
    /*             |      0 0 1 2 3 3 3 4 4 4 4 4 4 4 3 3 2 2 1 0 0        |                                                  */
    /*             |        0 1 1 2 2 3 3 3 3 3 3 3 3 3 2 2 1 1 0          |                                                  */
    /*         -80 +          0 1 1 2 2 3 3 3 3 3 3 3 2 2 1 1 0            +  -80                                             */
    /*             |          0 0 1 1 2 2 2 2 2 2 2 2 2 1 1 0 0            |                                                  */
    /*             |            0 0 0 0 0 1 1 1 1 1 0 0 0 0 0              |                                                  */
    /*             |                    0 0 0 0 0 0 0                      |                                                  */
    /*             |                                                       |                                                  */
    /*        -180 +                                                       + -180                                             */
    /*             -+--------+--------+--------+--------+--------+--------+-                                                  */
    /*            -180     -120      -60       0       60       120      180                                                  */
    /*                                       X_MM                                                                             */
    /*                                            m                                                                           */
    /*                                    -----                                                                               */
    /*                                    PHASE                                                                               */
    /*                                    -----                                                                               */
    /*              Plot of Y_MM*X_MM.  Symbol is value of DEGREES.                                                           */
    /*                                                                                                                        */
    /*                                      X_MM                                                                              */
    /*           -180     -120      -60       0       60       120      180                                                   */
    /*           --+--------+--------+--------+--------+--------+--------+--                                                  */
    /*      Y_MM |  PHASE OF WAVE FORM       QUINTILE  DEGREES _RANGE      |                                                  */
    /*           |                           ----------------------------- |                                                  */
    /*           |                              0      -175.04 <= -126.62  |                                                  */
    /*           |                              1      -116.69 <= -68.27   |                                                  */
    /*           |                              2      -58.35 <= 58.35     |                                                  */
    /*           |                              3      68.27 <= 116.69     |                                                  */
    /*           |                              4      126.62 <= 175.04    |                                                  */
    /*      Y_MM |                                                         | Y_MM                                             */
    /*           |                                                         |                                                  */
    /*       140 +                      1 2 2   2 2 3                      +  140                                             */
    /*       126 +                  0 1 1 2 2   2 2 3 3  4                 +  126                                             */
    /*       112 +             4 0  0 1 1 2 2   2 2 3 3  4 4 0             +  112                                             */
    /*        98 +           4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0           +   98                                             */
    /*        84 +           4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0           +   84                                             */
    /*        70 +         3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1         +   70                                             */
    /*        56 +         3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1         +   56                                             */
    /*        42 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +   42                                             */
    /*        28 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +   28                                             */
    /*        14 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +   14                                             */
    /*         0 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +    0                                             */
    /*       -14 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +  -14                                             */
    /*       -28 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +  -28                                             */
    /*       -42 +       3 3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1 1       +  -42                                             */
    /*       -56 +         3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1         +  -56                                             */
    /*       -70 +         3 4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0 1         +  -70                                             */
    /*       -84 +           4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0           +  -84                                             */
    /*       -98 +           4 4 0  0 1 1 2 2   2 2 3 3  4 4 0 0           +  -98                                             */
    /*       112 +             4 0  0 1 1 2 2   2 2 3 3  4 4 0             +  112                                             */
    /*       126 +                  0 1 1 2 2   2 2 3 3  4                 +  126                                             */
    /*       140 +                      1 2 2   2 2 3                      +  140                                             */
    /*           |                                                         |                                                  */
    /*           --+--------+--------+--------+--------+--------+--------+--                                                  */
    /*           -180     -120      -60       0       60       120      180                                                   */
    /*                                      X_MM                                                                              */
    /**************************************************************************************************************************/

    /*
    | | ___   __ _
    | |/ _ \ / _` |
    | | (_) | (_| |
    |_|\___/ \__, |
             |___/
    */

    1                                          Altair SLC          11:59 Tuesday, July 28, 2026

    NOTE: Copyright 2002-2025 World Programming, an Altair Company
    NOTE: Altair SLC 2026 (05.26.01.00.000758)
          Licensed to Roger DeAngelis
    NOTE: This session is executing on the X64_WIN11PRO platform and is running in 64 bit mode

    NOTE: AUTOEXEC processing beginning; file is C:\wpsoto\autoexec.sas
    NOTE: Library workx assigned as follows:
          Engine:        SAS7BDAT
          Physical Name: d:\wpswrkx

    NOTE: Library wpdx assigned as follows:
          Engine:        WPD
          Physical Name: d:\wpswrkx

    NOTE: Library slchelp assigned as follows:
          Engine:        WPD
          Physical Name: C:\Progra~1\Altair\SLC\2026\sashelp


    LOG:  11:59:06
    NOTE: 1 record was written to file PRINT

    NOTE: The data step took :
          real time : 0.022
          cpu time  : 0.031


    NOTE: Format num2mis output
    NOTE: Format $chr2mis output
    NOTE: Procedure format step took :
          real time : 0.014
          cpu time  : 0.000


    NOTE: AUTOEXEC processing completed

    1         /*--- COMPUTE THE QUINTILES FOR BOTH MAGNITUDE(WAVE AMPLITUDE) AND PHASE_DEG(WAVE FORM) ---*/
    2
    3         proc rank data=workx.anten(where=(magnitude>0 and phase_deg not in (0,180)))
    4                   out=workx.quintiles
    5                   groups=5;
    6             var magnitude phase_deg;
    7             ranks quintile degrees ;
    8         run;
    NOTE: 336 observations were read from "WORKX.anten"
    NOTE: Data set "WORKX.quintiles" has 336 observation(s) and 6 variable(s)
    NOTE: Procedure rank step took :
          real time : 0.010
          cpu time  : 0.000


    9
    10        /*--- CREATE THE LEGENDS ---*/
    11
    12        options nolabel;
    13        proc sql;
    14          select
    15            'magnitude' as group
    16            ,quintile
    17            ,catx(' ',put(min(magnitude),6.2),'<=',put(max(magnitude),6.2)) as QUINTILE_RANGE
    18          from
    19             workx.quintiles
    20          group
    21             by quintile
    22          union
    23             corr
    24          select
    25            'degrees' as group
    26            ,degrees as quintile
    27            ,catx(' ',put(min(phase_deg),7.2),'<=',put(max(phase_deg),7.2)) as QUINTILE_RANGE
    28          from
    29             workx.quintiles
    30          group
    31             by degrees
    32        ;quit;
    NOTE: Procedure sql step took :
          real time : 0.158
          cpu time  : 0.140


    33
    34
    35        /*--- PLOT  ---*/
    36
    37        options ls=64  ps=44;
    38        proc plot data=workx.quintiles;
    39         plot y_mm*x_mm=quintile/box
    40           haxis=-180 to 180 by 60;
    41        run;
    NOTE: Procedure plot step took :
          real time : 0.015
          cpu time  : 0.000


    42
    43        proc plot data=workx.quintiles;
    44         plot y_mm*x_mm=degrees/box
    45           haxis=-180 to 180 by 60;
    46        run;
    NOTE: Procedure plot step took :
          real time : 0.013
          cpu time  : 0.000


    47        options ls=255 ps=255;
    48

    NOTE: Submitted statements took :
          real time : 0.305
          cpu time  : 0.265

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
