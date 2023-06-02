Geometry:
    N = 512
    max_angle = 360
    num_angle = 600
    du = 0.24
    SOD = 393
    SDD = 600
    nBins = 1350
    angles = np.linspace(0, max_angle / 180 * np.pi, num_angle, False)
    
ASTRA usage example:
    vol_geom = astra.create_vol_geom(N, N)
    proj_geom = astra.create_proj_geom('fanflat', du, nBins, angles, SOD, SOD-SDD)
    proj_id = astra.create_projector('line_fanflat', proj_geom, vol_geom)
    
Read sinograms:
    saveFileName = #'IMAGEDIRIMAGEDIRIMAGEDIRIMAGEDIR'
    sinogram = np.fromfile(saveFileName, dtype = np.float32).reshape([num_angle, nBins])
    sinogram_id = astra.data2d.create('-sino', proj_geom, sinogram)
