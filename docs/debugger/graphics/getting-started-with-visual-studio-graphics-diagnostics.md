---
title: Začínáme s diagnostikou grafiky | Microsoft Docs
description: Připravte se na použití Diagnostika grafiky poprvé a potom Zachyťte snímky z aplikace Direct3D a prověřte je v analyzátoru grafiky.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70512b4df3be7f11973af244c336b22c59c90f8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387603"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Začínáme s diagnostikou grafiky sady Visual Studio
V této části se budete připravit na použití Diagnostika grafiky poprvé, budete zachytit snímky z aplikace Direct3D a prozkoumávat je v analyzátoru grafiky.

## <a name="requirements"></a>Požadavky
 Chcete-li použít Diagnostika grafiky v aplikaci Visual Studio, je nutné použít Visual Studio Enterprise, Visual Studio Professional nebo Visual Studio Community.  Jiné edice, včetně Visual Studio Code, tuto funkci neobsahují.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Požadavky Windows 10
 Volitelné *nástroje grafiky* funkcí Windows poskytují infrastrukturu zachytávání a přehrávání, kterou vyžaduje Diagnostika grafiky ve Windows 10.

 Informace o instalaci nástrojů grafiky najdete v tématu [Instalace nástrojů grafiky pro Windows 10](#InstallGraphicsTools).

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Instalace nástrojů grafiky pro Windows 10
 Ve Windows 10 je infrastruktura Diagnostika grafiky poskytovaná volitelnou funkcí Windows s názvem *Graphics Tools*. Tato funkce je nutná k zaznamenání a přehrání grafické informace ve Windows 10 bez ohledu na to, jestli je aplikace zachycená v předchozí verzi Windows nebo kterou verzi rozhraní Direct3D používá. Můžete si vybrat, že chcete nainstalovat funkci nástrojů grafiky předem. v opačném případě se nainstaluje na vyžádání při prvním spuštění relace Diagnostika grafiky ze sady Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Instalace nástrojů grafiky pro Windows 10

1. Do pole Hledat zadejte **aplikace a funkce** a pak otevřete nastavení **aplikace & funkce** .

2. Na pravé straně okna **aplikace & funkce** vyberte možnosti **volitelné funkce** (v části **aplikace & funkce**).

   Zobrazí se nastavení **volitelné funkce** .

3. V nastavení **volitelné funkce** vyberte možnost **Přidat funkci**. Zobrazí se seznam volitelných funkcí, které můžete nainstalovat.

4. V seznamu funkcí vyberte **nástroje grafiky** a pak zvolte **nainstalovat**.

   Funkce Graphics Tools je také automaticky nainstalována při instalaci sady Windows 10 SDK.

> [!TIP]
> Volitelná funkce Graphics Tools systému Windows 10 poskytuje funkce prostého zachytávání a přehrávání, jako je například program pro zachycení příkazového řádku **dxcap.exe**, který se dá použít v scénářích podpory, testování a diagnostiky na počítačích, kde nejsou nainstalované vývojářské nástroje. Další informace najdete v tématu [Nástroj pro zachycení z příkazového řádku](command-line-capture-tool.md) .

## <a name="using-graphics-diagnostics-for-the-first-time"></a>První použití Diagnostika grafiky
 Teď, když máte všechno, co potřebujete, jste připraveni začít používat Diagnostika grafiky. Postupujte podle těchto kroků.

### <a name="1---create-a-direct3d-app"></a>1. Vytvoření aplikace Direct3D

Pokud už máte vlastní aplikaci Direct3D, abyste prozkoumali Diagnostika grafiky s, Skvělé! V opačném případě použijte jednu z následujících možností:

::: moniker range=">=vs-2019"
Stáhněte si ukázku ze [hry Direct3D Sample](/samples/microsoft/windows-universal-samples/simple3dgamedx/).
::: moniker-end
::: moniker range="vs-2017"
- Šablony projektů aplikace **DirectX 11 (univerzální pro Windows)** nebo **aplikace DirectX 12 (univerzální pro Windows)** pro Windows 10.
- [Ukázka Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) pro Windows 10
::: moniker-end

Ujistěte se, že aplikaci můžete sestavit a spustit před přechodem na. Vyberte **sestavit** sestavení  >  **řešení** a ujistěte se, že se sestaví bez chyb. Pak zvolte **ladit**  >  **Spustit bez ladění** (**CTRL + F5**) a ujistěte se, že funguje správně. V závislosti na tom, který počítač testujete pomocí nástroje, možná budete muset upravit platformu a cíl ladění pro ukázku. Chcete-li například testovat platformu x64 na hostitelském počítači sady Visual Studio, jako cíl ladění vyberte možnost **x64** jako platformu řešení a **místní počítač** . 

### <a name="2---start-a-graphics-diagnostics-session"></a>2. spuštění relace Diagnostika grafiky
 Teď jste připraveni začít svoji první relaci diagnostiky grafiky. V aplikaci Visual Studio v hlavní nabídce zvolte možnost **ladění, grafika, spustit ladění grafiky** nebo stačí stisknout klávesy **ALT + F5**. Tím se aplikace spustí v rámci Diagnostika grafiky a zobrazí okna diagnostické relace v aplikaci Visual Studio.

> [!IMPORTANT]
> Pokud aplikaci spouštíte ve Windows 10 a ještě nemáte nainstalovanou funkci volitelné grafické nástroje, zobrazí se vám výzva k tomu, abyste to provedli nyní. Než budete moct použít Diagnostika grafiky ve Windows 10, musíte ho nainstalovat.

### <a name="3---capture-frames"></a>3. zachytávání snímků
 Jste připraveni zachytit snímky hned po spuštění aplikace.

#### <a name="to-capture-single-frames"></a>Zachycení jednoho rámce

- V sadě Visual Studio vyberte tlačítko **zachytit snímek** z panelu nástrojů grafiky nebo okna relace diagnostiky. Nebo pokud má vaše aplikace fokus, stačí stisknout na klávesnici klávesu **Print Screen** .

#### <a name="to-capture-a-sequence-of-frames"></a>Zachycení posloupnosti snímků

- V sadě Visual Studio v okně diagnostická relace nastavte **snímky pro zachycení** na počet snímků, které chcete zachytit v sekvenci, a potom Zachyťte sekvenci pomocí kterékoli z metod, které jste si popsali výše, abyste mohli zachytit jednotlivé snímky.

   Pokud chcete zachytit jeden snímek znovu, nastavte **snímky pro zachycení** na *1*.

  Až zachytíte snímky, ukončete aplikaci nebo klikněte na tlačítko **zastavit** z panelu nástrojů grafiky nebo okna relace diagnostiky.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4. prověřte zachycené snímky v analyzátoru grafiky
 Teď jste připraveni zkontrolovat snímky, které jste právě zachytili. Chcete-li zahájit analýzu snímku, vyberte číslo rámce rámce, který chcete prošetřit z okna diagnostické relace. Tím se otevře rámec v **analyzátoru grafiky**, kde můžete pomocí Diagnostika grafikych nástrojů zjistit, jak vaše aplikace využívá Direct3D ke sledování problémů s vykreslováním, nebo použít nástroj pro **analýzu snímků** k pochopení jeho výkonu.

 Pokud jste vybrali špatný rámec z okna diagnostické relace nebo chcete prošetřit jiný snímek, můžete z analyzátoru grafiky vybrat nový. Na kartě **cíl vykreslování** okna log Graphics v části Obrázek cíle vykreslování rozbalte **seznam rámců** a zvolte jiný rámec, který chcete prošetřit.

 Další informace o tom, jak používat nástroje analyzátoru grafiky společně, najdete v [příkladech](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Viz také
- [Technologie Direct3D 12 Graphics](/windows/desktop/direct3d12/direct3d-12-graphics)