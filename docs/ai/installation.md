---
title: Nainstalovat nástroje AI
description: Popisuje instalaci nástrojů AI pro Visual Studio.
keywords: AI, Visual Studio
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: fb296346d54b0774bdd9a738581ee28fe99b1de0
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777474"
---
# <a name="installation"></a>Instalace

Visual Studio Tools for AI lze nainstalovat na 64bitové operační systémy 64 Windows.

## <a name="install-visual-studio-tools-for-ai"></a>Nainstalovat Visual Studio Tools for AI

Toto rozšíření spolupracuje s Visual Studiem 2015 a sadou Visual Studio 2017, Community Edition nebo vyšší.

Nástroje si můžete stáhnout z [Visual Studio Marketplace](https://aka.ms/vstoolsforai)nebo z aplikace Visual Studio:

1. Vyberte **nástroje**  > **rozšíření a aktualizace**.

   ![Nabídka rozšíření a aktualizace v aplikaci Visual Studio](media/installation/extensions.png)

2. V dialogovém okně **rozšíření a aktualizace** vyberte **online** na levé straně.
3. Do vyhledávacího pole v pravém horním rohu zadejte nebo zadejte "Tools for AI".
4. Z výsledků vyberte **Visual Studio Tools for AI** .
5. Klikněte na tlačítko **Stáhnout**.

## <a name="prepare-your-local-machine"></a>Příprava místního počítače

Před školením modelů s hloubkovým učením v místním počítači se ujistěte, že máte nainstalované příslušné předpoklady. To zahrnuje, že budete mít k dispozici nejnovější ovladače a knihovny pro grafický procesor NVIDIA (pokud ho máte). Také se ujistěte, že máte nainstalované knihovny Pythonu a Pythonu, jako je NumPy, SciPy, a příslušné architektury hloubkového učení, jako je například Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch a chainer, které plánujete použít ve vašem projektem.

> [!NOTE]
> Představení softwaru v následujících pododdílech je výňatkem z jejich domovské stránky.

### <a name="nvidia-gpu-driver"></a>Ovladač NVIDIA GPU

Architektury hloubkového učení využívají grafický procesor NVIDIA, aby se počítače urychlily rychlostí, přesností a škálováním na skutečné umělé poznatky. Pokud má počítač karty NVIDIA GPU, přečtěte si téma [Stažení ovladačů NVIDIA](https://www.nvidia.com/Download/index.aspx) nebo zkuste nainstalovat nejnovější ovladač aktualizací operačního systému.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) je platforma pro paralelní výpočetní prostředí a programovací model vymysleli pomocí NVIDIA. Díky využití síly GPU může výrazně zvýšit výkon výpočetního výkonu. V současnosti jsou CUDA Toolkit 8,0 vyžadovány architekturou pro hloubkové učení.

Instalace CUDA

- Navštivte tento [Web](https://developer.nvidia.com/cuda-80-ga2-download-archive), Stáhněte si CUDA a nainstalujte ho.
- Nezapomeňte nainstalovat knihovny runtime CUDA a pak přidat binární cestu CUDA do proměnné prostředí% PATH% nebo $Path.
- Ve Windows je ve výchozím nastavení tato cesta "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

![Instalace CUDA ve Windows](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (CUDA neuronové Network Library) je knihovna primitivních primitiv pro rozsáhlou neuronové síť s grafickým procesorem (NVIDIA). cuDNN V6 vyžaduje nejnovější architektury hloubkového učení.

Instalace cuDNN:

- Navštivte [vývojáře NVIDIA](https://developer.nvidia.com/rdp/cudnn-download) a stáhněte a nainstalujte si nejnovější balíček.
- Zajistěte Přidání adresáře obsahujícího binární soubor cuDNN do proměnné prostředí% PATH% nebo $Path.
- V systému Windows můžete zkopírovat cudnn64_6. dll do složky C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin.

> [!NOTE]
> Předchozí architektury hloubkového učení, jako jsou CNTK 2,0 a TensorFlow 1.2.1, potřebují cuDNN v 5.1. Můžete však nainstalovat více verzí cuDNN dohromady.

### <a name="python"></a>Python

Python byl primárním programovacím jazykem pro aplikace s hloubkovým učením. **64 – bit** Pro zajištění nejlepší kompatibility se doporučuje distribuce Pythonu a [3.5.4 Pythonu](https://www.python.org/downloads/release/python-354/) .

### <a name="to-install-python-on-windows"></a>Instalace Pythonu ve Windows

- Doporučujeme nainstalovat spouštěč Pythonu jenom pro sebe a přidat Python do proměnné prostředí% PATH%.
- Nezapomeňte nainstalovat PIP, což je systém správy balíčků pro instalaci a správu softwarových balíčků napsaných v Pythonu.

Architektury hloubkového učení využívají PIP pro vlastní instalaci.

![Instalace Pythonu ve Windows](media/installation/install_python_win.png)

Pak musíme ověřit, jestli je Python 3,5 nainstalovaný správně, a upgradovat PIP na nejnovější verzi spuštěním následujících příkazů v terminálu:

- **Windows**

  ```cmd
  C:\Users\test>python -V
  Python 3.5.4

  C:\Users\test>pip3.5 -V
  pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

  C:\Users\test>python -m pip install -U pip
  ```

- **macOS**

  ```bash
  MyMac:~ test$ python3.5 -V
  Python 3.5.4

  MyMac:~ test$ pip3.5 -V
  pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

  MyMac:~ test$ python3.5 -m pip install -U pip
  ```

### <a name="python-on-visual-studio"></a>Python v aplikaci Visual Studio

Python je plně podporovaný v aplikaci Visual Studio prostřednictvím rozšíření.
Další informace najdete v o instalaci [Pythonu pro Visual Studio Tools](../python/installing-python-support-in-visual-studio.md) .

### <a name="numpy-and-scipy"></a>NumPy a SciPy

- **Numpy** je univerzální balíček pro zpracování polí určený k efektivní manipulaci s velkými multidimenzionálními poli libovolných záznamů, aniž by došlo k omezení příliš velkého počtu malých multidimenzionálních polí.

- **SciPy** ("sigh koláč") je open source software pro matematické, vědecké a inženýry v závislosti na numpy. Od verze 1.0.0 nyní má SciPy oficiální předem sestavený balíček pro Windows.

Pokud chcete nainstalovat NumPy a SciPy, spusťte v terminálu následující příkaz:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Výše uvedený příkaz upgraduje stávající staré nebo neoficiální (např. balíčky třetích stran z http://www.lfd.uci.edu/~gohlke/pythonlibs/ pro Windows) NumPy a SciPy na nejnovější oficiální.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) je jednotná sada nástrojů pro hloubkové učení, která popisuje sítě neuronové jako řadu výpočetních kroků prostřednictvím řízeného grafu. CNTK podporuje programovací jazyky Python i BrainScript.

> [!NOTE]
> CNTK v současné době nepodporuje macOS.

Pokud chcete nainstalovat balíček Pythonu CNTK, přečtěte si [článek Jak nainstalovat CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine).

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) je open source softwarová knihovna pro numerické výpočty pomocí grafů toku dat. Podrobnější informace o instalaci najdete [tady](https://www.tensorflow.org/install/) .

> [!NOTE]
> Od verze 1,2 už TensorFlow neposkytuje podporu GPU pro macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) je odlehčená, modulární a škálovatelná architektura pro hloubkové učení. Caffe2 se sestavuje na původním Caffe a je navržena s ohledem na výraz, rychlost a modularitu.

V současné době není k dispozici žádný předem sestavený balíček Caffe2 Pythonu.

Pokud chcete sestavit ze zdrojového kódu, přejděte [sem](https://caffe2.ai/docs/getting-started.html) .

### <a name="mxnet"></a>MXNet

[Apache MXNet (inkubace)](https://mxnet.incubator.apache.org/) je rozhraní pro hloubkové učení navržené pro zajištění efektivity i flexibility. Umožňuje **kombinovat** [symbolické a imperativní programování](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) , aby bylo možné maximalizovat efektivitu a produktivitu.

Pokud chcete nainstalovat MXNet, spusťte v terminálu následující příkaz:

- S grafickým procesorem

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- Bez GPU

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) je rozhraní API pro neuronové sítě vysoké úrovně, které je napsané v Pythonu, které je schopné provozovat v CNTK, TensorFlow nebo Theano. Byla vyvinuta se zaměřením na povolení rychlého experimentu. Možnost jít z nápadu na výsledek s nejmenším možným zpožděním je klíč k zajištění dobrého výzkumu.

Pokud chcete nainstalovat Keras, spusťte v terminálu následující příkaz:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) je knihovna Pythonu, která umožňuje efektivně definovat, optimalizovat a vyhodnocovat matematické výrazy, které zahrnují multidimenzionální pole.

Pokud chcete nainstalovat Theano, spusťte v terminálu následující příkaz:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](https://pytorch.org/) je balíček Pythonu, který poskytuje dvě funkce na nejvyšší úrovni:

- Tensor výpočet (jako NumPy) se silným zrychlením GPU
- Špičkové sítě neuronové postavené na páskovém systému automatického třídění

Pokud chcete nainstalovat PyTorch, spusťte v terminálu následující příkaz:

- **Windows**

  Ještě není k dispozici žádný oficiální balíček kolečka. Balíček třetí strany si můžete stáhnout z [Anaconda](https://anaconda.org/pytorch/repo?type=all) nebo [univerzity Kalifornie](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch).

  - Dekomprimujte ho do svého domovského adresáře, například *C:\Users\test\pytorch*.
  - Přidejte *C:\Users\test\pytorch\Lib\site-Packages* do proměnné prostředí% PYTHONPATH%.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **macOS**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > binární soubory macOS nepodporují CUDA. Pokud potřebujete CUDA, nainstalujte ze zdroje.

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > Tento jediný balíček podporuje GPU i procesor.

Nakonec nainstalujte torchvision na jiný systém než Windows:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>chainer

[Chainer](https://chainer.org/) je architektura pro hloubkové učení založená na Pythonu, která je zaměřená na flexibilitu. Poskytuje Automatická rozlišení rozhraní API na základě definice přístupu definovaného po spuštění (označované také jako dynamické výpočetní grafy), stejně jako rozhraní API na vysoké úrovni pro vytváření a výukové neuronové sítě.

Pokud chcete povolit podporu CUDA, nainstalujte [CuPy](https://github.com/cupy/cupy):

```bash
pip3.5 install cupy
```

> [!NOTE]
> Ve Windows potřebujete verzi 2015 sady [Visual Studio](https://visualstudio.microsoft.com/) nebo [nástroje C++ Microsoft Visual Build](https://visualstudio.microsoft.com/visual-cpp-build-tools/) pro kompilaci CuPy s CUDA 8,0.

Pokud chcete nainstalovat chainer, spusťte v terminálu následující příkaz:

```bash
pip3.5 install chainer==3.0.0
```
