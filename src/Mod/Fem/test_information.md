# FEM unit test information
- Find in this fils some informatin how to run unit test for FEM

## more information 
- how to run a specific test class or a test method see file
- src/Mod/Test/__init__
- forum https://forum.freecadweb.org/viewtopic.php?f=10&t=22190#p175546

## let some test document stay open
- run test method from inside FreeCAD
- in tearDown method to not close the document
- temporary comment FreeCAD.closeDocument(self.doc_name) and add pass


## unit test command to copy
- to run a specific FEM unit test to copy for fast tests :-)
- they can be found in file test_commands_to_copy.md
- greate them by

```python
from femtest.app.support_utils import get_fem_test_defs
get_fem_test_defs()
```

## examples from within FreeCAD:
### create all objects test
```python
import Test, femtest.app.test_object
Test.runTestsFromClass(femtest.app.test_object.TestObjectCreate)
```

### all FEM tests
```python
import Test, TestFemApp
Test.runTestsFromModule(TestFemApp)
```

### module
```python
import Test, femtest.app.test_common
Test.runTestsFromModule(femtest.app.test_common)
```

### class
```python
import Test, femtest.app.test_common
Test.runTestsFromClass(femtest.app.test_common.TestFemCommon)
```

### method
```python
import unittest
thetest = "femtest.app.test_common.TestFemCommon.test_pyimport_all_FEM_modules"
alltest = unittest.TestLoader().loadTestsFromName(thetest)
unittest.TextTestRunner().run(alltest)
```

## examples from shell in build dir:
### all FreeCAD tests
```python
./bin/FreeCADCmd --run-test 0
./bin/FreeCAD --run-test 0
```

### all FEM tests
```bash
./bin/FreeCADCmd --run-test "TestFemApp"
./bin/FreeCAD --run-test "TestFemApp"
```

### import Fem and FemGui
```bash
./bin/FreeCADCmd --run-test "femtest.app.test_femimport"
./bin/FreeCAD --run-test "femtest.app.test_femimport"
```

### module
```bash
./bin/FreeCAD --run-test "femtest.app.test_femimport"
```

### class
```bash
./bin/FreeCAD --run-test "femtest.app.test_common.TestFemCommon"
```

### method
```bash
./bin/FreeCAD --run-test "femtest.app.test_common.TestFemCommon.test_pyimport_all_FEM_modules"
```

### Gui
```bash
./bin/FreeCAD --run-test "femtest.gui.test_open.TestObjectOpen"
```


## open files 
### from FEM test suite source code
- be careful on updating these files, they contain the original results!
- TODO update files, because some of them have non-existing FEM object classes

```python
doc = FreeCAD.open(FreeCAD.ConfigGet("AppHomePath") + 'Mod/Fem/femtest/data/ccx/cube.FCStd')
doc = FreeCAD.open(FreeCAD.ConfigGet("AppHomePath") + 'Mod/Fem/femtest/data/ccx/cube_frequency.FCStd')
doc = FreeCAD.open(FreeCAD.ConfigGet("AppHomePath") + 'Mod/Fem/femtest/data/ccx/cube_static.FCStd')
doc = FreeCAD.open(FreeCAD.ConfigGet("AppHomePath") + 'Mod/Fem/femtest/data/ccx/Flow1D_thermomech.FCStd')
doc = FreeCAD.open(FreeCAD.ConfigGet("AppHomePath") + 'Mod/Fem/femtest/data/ccx/multimat.FCStd')
doc = FreeCAD.open(FreeCAD.ConfigGet("AppHomePath") + 'Mod/Fem/femtest/data/ccx/spine_thermomech.FCStd')
```


### generated from test suite
```python
import femtest.utilstest as ut
ut.all_test_files()

doc = ut.cube_frequency()
doc = ut.cube_static()
doc = ut.Flow1D_thermomech()
doc = ut.multimat()
doc = ut.spine_thermomech()
```

### load std FEM example files
```python
app_home = FreeCAD.ConfigGet("AppHomePath")
doc = FreeCAD.open(app_home + "data/examples/FemCalculixCantilever2D.FCStd")
doc = FreeCAD.open(app_home + "data/examples/FemCalculixCantilever3D.FCStd")
doc = FreeCAD.open(app_home + "data/examples/FemCalculixCantilever3D_newSolver.FCStd")
doc = FreeCAD.open(app_home + "data/examples/Fem.FCStd")
doc = FreeCAD.open(app_home + "data/examples/Fem2.FCStd")
```

### load all documents files
```python
app_home = FreeCAD.ConfigGet("AppHomePath")
doc = FreeCAD.open(FreeCAD.ConfigGet("AppHomePath") + 'Mod/Fem/femtest/data/open/all_objects_de9b3fb438.FCStd')
```
