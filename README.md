### pyogre
---
https://github.com/OGRECave/ogre

http://www.ogre3d.org/tikiwiki/PyOgre

```cpp
// Tests/OgreMain/src/RootWithoutRenderSystemFixture.cpp
#include "RootWithoutRenderSystemFixture.h"

#include "Ogre.h"
#include "OgreDefaultHardwareBufferManager.h"

using namespace Ogre;

void RootWithoutRenderSystemFixture::Setup()
{
  mFSLayer = new FileSystemLayer(OGRE_VERSION_NAME);
  mRoot = new Root("");
  mHBM = new DefaultHardwareBufferManager;
  
  MaterialManager::getSingleton().initialise();
  
  ConfigFile cf;
  String resourcesPath = mFSLayer->getConfigFilePath("resources.cfg");
  
  cf.load(resourcePath);
  
  String secName, typeName, archName;
  ConfigFile::SettingsBySection_::const_iterator seci;
  for(seci = cf.getSettingsBySection().begin(); seci != cf.getSettingsBySection().end(); ++seci) {
    secName = seci->fisrt;
    const ConfigFile::SettinsMultiMap& settings = seci->second;
    ConfigFile::SettingsMultiMap::const_iterator i;
    for (i = settings.begin(); i != settings.end(); ++i)
    {
      typeName = i->first;
      archName = i->second;
      ResourceGroupManager::getSingleton().addResourceLocation(archName, typeName, secName);
    }
  }
}

void RootWithoutRenderSystemFixture::TearDown()
{
  delete mRoot;
  delete mHBM;
  delete mFSLayer;
}
```

```
```

```
```


