---
title: Instalace nástroje AI
description: Popisuje postup instalace nástroje AI pro sadu Visual Studio
keywords: AI, visual studio
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 465443211d1a3f1aff8bfa63fa6cb8068b55980b
ms.sourcegitcommit: 551f13774e8bb0eb47cbd973745628a956e866aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459761"
---
# <a name="installation"></a>Instalace

Visual Studio Tools for AI je nainstalovat v operačních systémech Windows 64-bit.

## <a name="install-visual-studio-tools-for-ai"></a>Instalace sady Visual Studio Tools pro AI

Toto rozšíření funguje s Visual Studio 2015 a Visual Studio 2017 Community edition nebo vyšší.

Můžete si stáhnout nástroje od [Visual Studio Marketplace](http://aka.ms/vstoolsforai), nebo z v rámci sady Visual Studio:

1. Vyberte **nástroje** > **rozšíření a aktualizace**.

   ![Rozšíření a aktualizace nabídky v sadě Visual Studio](media/installation/extensions.png)

2. V **rozšíření a aktualizace** dialogu **Online** na levé straně.
3. Do vyhledávacího pole v pravém horním rohu typ nebo zadejte "tools for ai".
4. Vyberte **Visual Studio Tools for AI** ve výsledcích.
5. Klikněte na tlačítko **Stáhnout**.

## <a name="prepare-your-local-machine"></a>Příprava místního počítače

Před trénování hloubkového učení modelů v místním počítači, ujistěte se, že máte příslušné nainstalovány požadované součásti. To zahrnuje, a ujistěte se, že máte nejnovější ovladače a knihovny pro váš grafický procesor NVIDIA (pokud nějakou máte). Měli byste také zajistit, je nainstalovaný Python a Python knihoven, jako je například NumPy, SciPy a odpovídající hloubkového učení architektury, jako jsou Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch a Chainer, který budete používat v váš projekt.

> [!NOTE]
> Představení softwaru v následujících oddílech je výňatkem z jeho domovské stránky.

### <a name="nvidia-gpu-driver"></a>Ovladač NVIDIA GPU

Architektury obsáhlého learningu využijte grafický procesor NVIDIA chcete, aby počítače další rychlostí, přesnost a škálovat směrem k true umělé inteligence. Pokud má počítač kartami NVIDIA GPU, navštivte prosím [tady](http://www.nvidia.com/Download/index.aspx) nebo zkuste operačního systému update nainstalujte nejnovější ovladač.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) je paralelní výpočetní platformy a programovací model vymysleli podle NVIDIA. Umožňuje výrazné zvýšení výpočetní výkon podle síly GPU. V současné době CUDA Toolkit 8.0 nevyžadovala architektury hloubkového učení.

Chcete-li nainstalovat CUDA

- Navštivte tuto [lokality](https://developer.nvidia.com/cuda-80-ga2-download-archive), CUDA stáhněte a nainstalujte ho.
- Ujistěte se, že k instalaci knihoven modulu runtime CUDA a pak přidejte CUDA binární cesty do proměnné % PATH % nebo $Path prostředí.
- Na Windows tato cesta je "C:\Program Files\NVIDIA GPU computingu Toolkit\CUDA\v8.0\bin" ve výchozím nastavení.

![Nainstalujte CUDA na Windows](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (knihovna CUDA hluboké Neuronové sítě) je knihovna – hardwarově akcelerovanou primitivních elementů pro hluboké neuronové sítě pomocí NVIDIA. cuDNN IPv6 vyžaduje nejnovější architektury hloubkového učení.

Chcete-li nainstalovat cuDNN:

- Navštivte [NVIDIA Developer](https://developer.nvidia.com/rdp/cudnn-download) stáhnete a nainstalujete nejnovější balíček.
- Nezapomeňte přidat adresář obsahující cuDNN binární do proměnné % PATH % nebo $Path prostředí.
- Na Windows můžete zkopírovat cudnn64_6.dll do "C:\Program Files\NVIDIA GPU computingu Toolkit\CUDA\v8.0\bin".

> [!NOTE]
> Předchozí architektur obsáhlého learningu CNTK 2.0 a TensorFlow 1.2.1 potřebovat cuDNN verze 5.1. Však můžete nainstalovat více verzí cuDNN společně.

### <a name="python"></a>Python

Python byl primární programovací jazyk pro obsáhlý learning aplikací. **64-bit** je povinný, distribuci jazyka Python a [Python 3.5.4](https://www.python.org/downloads/release/python-354/) se doporučuje pro nejlepší kompatibility.

### <a name="to-install-python-on-windows"></a>K instalaci Pythonu na Windows

- Jsme navrhnout instalace Spouštěč Pythonu pouze pro sebe a přidat Python do proměnné % PATH % prostředí.
- Zkontrolujte instalaci pip, což je systém správy balíčků, instalaci a správě softwarových balíčků, které jsou napsané v Pythonu.

Architektury obsáhlého learningu využívají pip pro vlastní instalaci.

![Nainstalovat Python ve Windows](media/installation/install_python_win.png)

Nakonec musíme ověřit, zda je správně nainstalován Python 3.5 a upgradovat na nejnovější verzi spuštěním následujících příkazů v terminálu:

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

### <a name="python-on-visual-studio"></a>Python v sadě Visual Studio

Je plně podporován Python v sadě Visual Studio prostřednictvím rozšíření.
Další informace o instalaci [Pythonu pro Visual Studio Tools](../python/installing-python-support-in-visual-studio.md) další podrobnosti.

### <a name="numpy-and-scipy"></a>NumPy a SciPy

- **NumPy** je navržená tak, aby efektivně pracovat s velké vícerozměrných polí záznamů libovolné aniž byste museli obětovat příliš mnoho rychlost pro malé vícerozměrných polí pro obecné účely zpracování pole balíček.

- **SciPy** (vyslovováno "Sigh výsečový") je open-source software pro matematiky, strojírenské a vědecké účely, v závislosti na NumPy. Od verze 1.0.0, SciPy má teď oficiální předem připravených wheel balíčku pro Windows.

Pokud chcete nainstalovat NumPy a SciPy, spusťte následující příkaz, v terminálu:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Výše uvedené příkaz upgrady stávajících starý nebo neoficiální (například balíčky třetích stran z http://www.lfd.uci.edu/~gohlke/pythonlibs/ pro Windows) NumPy a SciPy nejnovější oficiální ty.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) je jednotný nástrojů obsáhlého learningu, která popisuje neuronové sítě jako výpočetní kroky prostřednictvím orientovaného grafu řady. CNTK podporuje Python a BrainScript programovacích jazyků.

> [!NOTE]
> CNTK aktuálně nepodporuje macOS.

Chcete-li nainstalovat balíček Pythonu CNTK, přečtěte si téma [instalace CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) je open source knihovna softwaru pro numerické výpočty pomocí grafy toku dat. Odkazovat na [tady](https://www.tensorflow.org/install/) pro podrobnou instalaci.

> [!NOTE]
> Od verze 1.2 TensorFlow již poskytuje podporou GPU pro macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) je jednoduché, modulární a škálovatelné obsáhlého learningu rozhraní. Staví na původní Caffe, Caffe2 je navržená s výrazem, rychlost a modularitu v úvahu.

V současné době není k dispozici žádné předem připravených Caffe2 balíček wheel pythonu.

Navštivte [tady](https://caffe2.ai/docs/getting-started.html) k sestavení ze zdrojového kódu.

### <a name="mxnet"></a>MXNet

[Apache MXNet (incubating)](https://mxnet.incubator.apache.org/) je navržená pro efektivity a pružnosti rozhraní hloubkového učení. To vám umožní **kombinovat** [symbolické a imperativní programování](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) pro maximalizaci efektivity a produktivity.

Pokud chcete nainstalovat MXNet, spusťte následující příkaz, v terminálu:

- S GPU
    ```bash
    pip3.5 install mxnet-cu80==0.12.0
    ```
- Bez GPU
    ```bash
    pip3.5 install mxnet==0.12.0
    ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) je napsána v jazyce Python a schopný běžet na horní CNTK, TensorFlow nebo Theano rozhraní API vysoké úrovně neuronových sítí. Byl vyvinut se zaměřením na povolení rychlé experimentování. Schopnost od nápadu k výsledek s nejmenšími možnými zpoždění je klíčem k provádění dobré zdroje informací.

K instalaci Keras, spusťte v terminálu následující příkaz:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) je knihovna Python, který umožňuje definovat, optimalizovat a vyhodnotit matematické výrazy zahrnující vícerozměrných polí efektivně.

Pokud chcete nainstalovat Theano, spusťte následující příkaz v terminálu:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](http://pytorch.org/) je balíček python, který poskytuje dvě základní funkce:

- Výpočet tensor (např. numpy) díky akceleraci silné GPU
- Hluboké Neuronové sítě postavená na systému autograd založené na pásce

Pokud chcete nainstalovat PyTorch, spusťte následující příkaz, v terminálu:

- **Windows**
    - Dosud neexistuje žádné oficiální wheel balíčku. Můžete si stáhnout třetí strany [Anaconda PyTorch balíčku](https://anaconda.org/pytorch/repo?type=all).
    - Třeba dekomprimovat do svého domovského adresáře "C:\Users\test\pytorch".
    - Přidejte do proměnné prostředí % PYTHONPATH % "C:\Users\test\pytorch\Lib\site-packages".

- **macOS**
    ```bash
    pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
    ```
    > [!NOTE]
    > macOS binárních souborů není podpora CUDA, nainstalujte ze zdroje v případě potřeby CUDA

- **Linux**
    ```bash
    pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
    ```
    > [!NOTE]
    > Tento jeden balíček podporuje GPU a CPU.

Nakonec nainstalujte torchvision na jiných Windows:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) je zaměřené na flexibilitu rozhraní založené na Pythonu hloubkového učení. Poskytuje rozhraní API na základě automatickou diferenciací **definovat pomocí run přístup** (označovaný také jako dynamické výpočetní grafy) a také objektově orientované rozhraní API vysoké úrovně pro vytvoření a trénování neuronových sítí.

Chcete-li povolit podporu CUDA, nainstalovat [CuPy](https://github.com/cupy/cupy):

```bash
pip3.5 install cupy
```

> [!NOTE]
> Na Windows, musíte verzi 2015 [sady Visual Studio](https://visualstudio.microsoft.com/) nebo [Microsoft Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) ke kompilaci CuPy se spouští CUDA 8.0.

K instalaci Chainer, spusťte v terminálu následující příkaz:

```bash
pip3.5 install chainer==3.0.0
```