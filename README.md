# MOM6-CICE6 025 deg JRA55-do RYF ACCESS-OM3 configuration

**WARNING: This configuration is still under development and should not be used for production.**

See [`main` branch
README](https://github.com/COSIMA/MOM6-CICE6/blob/main/README.md) for usage
information.

## Features

- data atmosphere (DATM) = JRA55-do v1-4, RYF 1990-1991
- data runoff (DROF) = JRA55-do v1-4, RYF 1990-1991
- tripolar grid

## Requirements

This configuration requires payu v1.0.29 or greater to run correctly.

---
Most of the updates are sourced from discussions in [namelist-discussion](https://forum.access-hive.org.au/t/namelist-configuration-discussion-meeting/1917/9?u=minghangli). Some significant updates are highlighted below,

- surface boundary layer parameterisation: 
  - Instead of KPP used in CVmix project, current configuration implements an energetic constrained parameterisation of the surface boundary layer (EPBL), providing vertically diffusivity and viscosity, and the depth of active mixing (BL thickness).

- Removal of mesoscale eddy mixing parametersiations (e.g., `USE_MEKE=False`)
- Set `NK=50`. 
  - Ongoing: Another configuration with `NK=75` to match `ACCESS-OM2-01` - use `KDS75 z*` is running simultaneously,
- No parameters associated with `TIDES`
- `NUM_DIAG_COORDS=2` includes `z_star` and `rho_2` (not sure if this is relevant for `0.25deg`([https://github.com/COSIMA/MOM6-CICE6/issues/40#issuecomment-1996247784](https://github.com/COSIMA/MOM6-CICE6/issues/40#issuecomment-1996247784)))

---
Others:
- timesteps
  - baraclinic timestep dt: 900s
  - tracer timestep: 3600s
  - coupling timestep: 900s
  - ice dynamic timestep: 900s



