---
title: Instalace nástrojů AI
description: Popisuje, jak nainstalovat nástroje AI pro Visual Studio.
keywords: ai, vizuální studio
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: a83deb968811159cfaeddaf537624e21b37e98c7
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638580"
---
# <a name="installation"></a>Instalace

Visual Studio Tools for AI lze nainstalovat do 64bitových operačních systémů se systémem Windows.

## <a name="install-visual-studio-tools-for-ai"></a>Instalace nástrojů Sady Visual Studio pro umělou přípravu

Toto rozšíření funguje s Visual Studio 2015 a Visual Studio 2017, Community Edition nebo vyšší.

Nástroje si můžete stáhnout z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vstoolsai-vs2017)nebo z visual studia:

1. Vyberte**možnost Rozšíření a aktualizace** **nástrojů** > .

   ![Nabídka Rozšíření a aktualizace v sadě Visual Studio](media/installation/extensions.png)

2. V dialogovém okně **Rozšíření a aktualizace** vyberte **online** na levé straně.
3. Do vyhledávacího pole v pravém horním rohu zadejte nebo zadejte "nástroje pro ai".
4. Z výsledků vyberte **Nástroje visual studia pro umělou přípravu.**
5. Klepněte na tlačítko **Stáhnout**.

## <a name="prepare-your-local-machine"></a>Příprava místního počítače

Před trénování modelů hloubkového učení v místním počítači se ujistěte, že máte nainstalované příslušné požadavky. To zahrnuje ujistěte se, že máte nejnovější ovladače a knihovny pro NVIDIA GPU (pokud máte jeden). Také se ujistěte, že jste nainstalovali knihovny Pythonu a Pythonu, jako jsou NumPy, SciPy a vhodné architektury pro hluboké učení, jako jsou Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch a Chainer, které plánujete použít ve svém projektu.

> [!NOTE]
> Úvod softwaru v následujících podsekcích je výňatek z jejich domovských stránek.

### <a name="nvidia-gpu-driver"></a>Ovladač GRAFICKÉ KARTY NVIDIA

Rámce hlubokého učení využívají grafický procesor NVIDIA k tomu, aby se stroje učily rychlostí, přesností a měřítkem směrem ke skutečné umělé inteligenci. Pokud je v počítači grafické karty NVIDIA, přečtěte si informace [o stažení ovladače NVIDIA](https://www.nvidia.com/Download/index.aspx) nebo vyzkoušejte aktualizaci operačního systému a nainstalujte nejnovější ovladač.

### <a name="cuda"></a>Cuda

[CUDA](https://developer.nvidia.com/cuda-zone) je paralelní výpočetní platforma a programovací model vynalezený společností NVIDIA. Umožňuje dramatické zvýšení výpočetního výkonu využitím výkonu GPU. V současné době cuda toolkit 8.0 je vyžadována hluboké učení rámců.

Instalace cuda

- Navštivte tento [web](https://developer.nvidia.com/cuda-80-ga2-download-archive), stáhněte cuda a nainstalujte jej.
- Nezapomeňte nainstalovat knihovny runtime CUDA a pak přidat binární cestu CUDA do proměnné %PATH% nebo $Path prostředí.
- V systému Windows je tato cesta ve výchozím nastavení "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

![Instalace cuda v systému Windows](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (CUDA Deep Neural Network library) je gpu akcelerovaná knihovna primitivů pro hluboké neuronové sítě od NVIDIA. cuDNN v6 je vyžadováno nejnovějšími frameworky hlubokého učení.

Instalace cuDNN:

- Navštivte [nvidia developer](https://developer.nvidia.com/rdp/cudnn-download) a stáhněte a nainstalujte nejnovější balíček.
- Ujistěte se, že přidáte adresář obsahující binární soubor cuDNN do %PATH% nebo $Path proměnné prostředí.
- V systému Windows můžete cudnn64_6.dll zkopírovat do souboru C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

> [!NOTE]
> Předchozí architektury hlubokého učení, jako jsou CNTK 2.0 a TensorFlow 1.2.1, potřebují cuDNN v5.1. Můžete však nainstalovat více verzí cuDNN společně.

### <a name="python"></a>Python

Python byl primární programovací jazyk pro aplikace hlubokého učení. **64bitové** Je vyžadována distribuce Pythonu a [Python 3.5.4](https://www.python.org/downloads/release/python-354/) se doporučuje pro nejlepší kompatibilitu.

### <a name="to-install-python-on-windows"></a>Instalace Pythonu do Windows

- Doporučujeme nainstalovat spouštěč Pythonu pouze pro sebe a přidat Python do proměnné prostředí %PATH%.
- Ujistěte se, že nainstalovat pip, což je systém pro správu balíčků pro instalaci a správu softwarových balíčků napsaných v Pythonu.

Hluboké učení rámce spoléhají na pip pro jejich vlastní instalaci.

![Instalace Pythonu ve Windows](media/installation/install_python_win.png)

Potom musíme ověřit, zda je Python 3.5 správně nainstalován, a upgradovat pip na nejnovější verzi provedením následujících příkazů v terminálu:

- **Windows**

  ```cmd
  C:\Users\test>python -V
  Python 3.5.4

  C:\Users\test>pip3.5 -V
  pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

  C:\Users\test>python -m pip install -U pip
  ```

- **Macos**

  ```bash
  MyMac:~ test$ python3.5 -V
  Python 3.5.4

  MyMac:~ test$ pip3.5 -V
  pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

  MyMac:~ test$ python3.5 -m pip install -U pip
  ```

### <a name="python-on-visual-studio"></a>Python ve visual studiu

Python je plně podporován v Sadě Visual Studio prostřednictvím rozšíření.
Další informace o instalaci [Pythonu pro nástroje Visual Studia](../python/installing-python-support-in-visual-studio.md) najdete v dalších informacích.

### <a name="numpy-and-scipy"></a>NumPy a SciPy

- **NumPy** je univerzální balíček pro zpracování pole určený k efektivní manipulaci s velkými vícerozměrnými poli libovolných záznamů bez obětování příliš velké rychlosti pro malá vícerozměrná pole.

- **SciPy** (vyslovuje se "Sigh Pie") je open-source software pro matematiku, vědu a inženýrství, v závislosti na NumPy. Počínaje verzí 1.0.0 má scipy nyní oficiální předem sestavený balíček kol pro Windows.

Chcete-li nainstalovat NumPy a SciPy, spusťte v terminálu následující příkaz:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Výše uvedený příkaz upgraduje stávající staré nebo neoficiální (např. balíčky třetích stran z http://www.lfd.uci.edu/~gohlke/pythonlibs/ windows) NumPy a SciPy na nejnovější oficiální.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) je jednotná sada nástrojů pro hluboké učení, která popisuje neuronové sítě jako řadu výpočetních kroků prostřednictvím řízeného grafu. CNTK podporuje programovací jazyky Pythonu i BrainScriptu.

> [!NOTE]
> CNTK momentálně nepodporuje macOS.

Chcete-li nainstalovat balíček CNTK Python, podívejte [se, jak nainstalovat CNTK](/cognitive-toolkit/Setup-CNTK-on-your-machine).

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) je open-source softwarová knihovna pro numerické výpočty pomocí grafů toku dat. Podrobné informace naleznete [zde.](https://www.tensorflow.org/install/)

> [!NOTE]
> Od verze 1.2 tensorflow již neposkytuje podporu GPU pro macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) je lehký, modulární a škálovatelný rámec hlubokého učení. Caffe2, který vychází z původní kavárny Caffe, je navržen s ohledem na výraz, rychlost a modularitu.

V současné době není k dispozici žádný předem postavený balíček caffe2 python kola.

Navštivte [zde](https://caffe2.ai/docs/getting-started.html) stavět ze zdrojového kódu.

### <a name="mxnet"></a>MXNet

[Apache MXNet (inkubace)](https://mxnet.incubator.apache.org/) je rámec hlubokého učení navržený jak pro efektivitu, tak pro flexibilitu. Umožňuje kombinovat **mix** [symbolické a imperativní programování](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) pro maximalizaci efektivity a produktivity.

Chcete-li nainstalovat síť MXNet, spusťte v terminálu následující příkaz:

- S GPU

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- Bez GPU

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) je rozhraní API pro neuronové sítě na vysoké úrovni, napsané v Pythonu, které je schopné běžet na vrcholu CNTK, TensorFlow nebo Theano. Byl vyvinut se zaměřením na umožnění rychlého experimentování. Být schopen jít od nápadu k výsledku s co nejmenším zpožděním je klíčem k tomu dobrý výzkum.

Chcete-li nainstalovat Keras, spusťte v terminálu následující příkaz:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) je knihovna Pythonu, která umožňuje efektivně definovat, optimalizovat a vyhodnocovat matematické výrazy zahrnující vícerozměrná pole.

Chcete-li nainstalovat Theano, spusťte následující příkaz v terminálu:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](https://pytorch.org/) je python balíček, který poskytuje dvě funkce na vysoké úrovni:

- Tenzorová výpočetní doba (jako numpy) se silnou akcelerací GPU
- Deep Neural Networks postavené na páskovém autogradovém systému

Chcete-li nainstalovat PyTorch, spusťte v terminálu následující příkaz:

- **Windows**

  Ještě tu není žádný oficiální balíček kol. Balíček třetí strany si můžete stáhnout z [Anacondy](https://anaconda.org/pytorch/repo?type=all) nebo [Kalifornské univerzity](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch).

  - Dekomprimujte jej do domovského adresáře, například *C:\Users\test\pytorch*.
  - Přidejte *balíčky C:\Users\test\pytorch\Lib\site-packages* do proměnné prostředí %PYTHONPATH%.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **Macos**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > Binární soubory macOS nepodporují CUDA, nainstalujte ze zdroje, pokud je cuda potřeba

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > Tento jediný balíček podporuje gpu i cpu.

Nakonec nainstalujte torchvision na non-Windows:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) je pythonský rámec hlubokého učení zaměřený na flexibilitu. Poskytuje automatická diferenciační api založená na přístupu definovat podle spuštění (označované také jako dynamické výpočetní grafy) a také objektově orientovaná lana API vysoké úrovně pro vytváření a trénování neuronových sítí.

Chcete-li povolit podporu CUDA, nainstalujte [CuPy](https://github.com/cupy/cupy):

```bash
pip3.5 install cupy
```

> [!NOTE]
> V systému Windows potřebujete 2015 verze [Sady Visual Nebo](https://visualstudio.microsoft.com/) Microsoft Visual [C++ nástroje pro sestavení](https://visualstudio.microsoft.com/visual-cpp-build-tools/) cupy s CUDA 8.0.

Chcete-li nainstalovat Chainer, spusťte v terminálu následující příkaz:

```bash
pip3.5 install chainer==3.0.0
```
