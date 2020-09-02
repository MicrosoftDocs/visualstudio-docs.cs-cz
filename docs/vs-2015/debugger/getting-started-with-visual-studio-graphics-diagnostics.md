---
title: Začínáme s Diagnostika grafiky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9056fdae9d0eff55c572d8e38503d88269dbde3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704709"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Začínáme s diagnostikou grafiky sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V této části se budete připravit na použití Diagnostika grafiky poprvé, budete zachytit snímky z aplikace Direct3D a prozkoumávat je v analyzátoru grafiky.

## <a name="requirements"></a>Požadavky
 Chcete-li použít Diagnostika grafiky v aplikaci Visual Studio 2015, je nutné mít jednu z následujících edicí:

- Visual Studio 2015 Enterprise

- Visual Studio 2015 Professional

- Komunita sady Visual Studio 2015

  [!INCLUDE[downloadvs](../includes/downloadvs-md.md)]

### <a name="windows-10-prerequisites"></a>Požadavky Windows 10
 Volitelné *nástroje grafiky* funkcí Windows poskytují infrastrukturu zachytávání a přehrávání, kterou vyžaduje Diagnostika grafiky ve Windows 10.

 Informace o instalaci nástrojů grafiky najdete v tématu [Instalace nástrojů grafiky pro Windows 10](#InstallGraphicsTools).

### <a name="windows-81-prerequisites"></a>Windows 8.1 předpoklady
 Sada Windows Software Development Kit (SDK) pro Windows 8.1 poskytuje infrastrukturu zachytávání a přehrávání, kterou vyžaduje Diagnostika grafiky na Windows 8.1, a podporuje vývoj pro Windows 8.1 a Windows 8.

 [Stažení sady Windows Software Development Kit (SDK) pro Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)

 Chcete-li použít vzdálený počítač pro přehrávání s Windows 10 z vývojového počítače se systémem Windows 8.1, je nutné nainstalovat sadu Windows 10 SDK do vývojového počítače a funkci volitelných grafických nástrojů na počítači pro přehrávání.

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Instalace nástrojů grafiky pro Windows 10
 Ve Windows 10 je infrastruktura Diagnostika grafiky poskytovaná volitelnou funkcí Windows s názvem *Graphics Tools*. Tato funkce je nutná k zaznamenání a přehrání grafické informace ve Windows 10 bez ohledu na to, jestli je aplikace zachycená v předchozí verzi Windows nebo kterou verzi rozhraní Direct3D používá. Můžete si vybrat, že chcete nainstalovat funkci nástrojů grafiky předem. v opačném případě se nainstaluje na vyžádání při prvním spuštění relace Diagnostika grafiky ze sady Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Instalace nástrojů grafiky pro Windows 10

1. V nabídce **Start** klikněte na položku **Nastavení**. Zobrazí se dialogové okno **Nastavení** .

2. V dialogovém okně **Nastavení** zvolte možnost **systém**a pak v seznamu nastavení systému vyberte **nainstalované aplikace** .

3. Na pravé straně dialogového okna **Nastavení** vyberte **Spravovat volitelné funkce** v části **nainstalované aplikace a funkce**. Zobrazí se dialogové okno **Spravovat volitelné funkce** .

4. V dialogovém okně **Spravovat volitelné funkce** vyberte možnost **Přidat funkci**. Zobrazí se seznam volitelných funkcí, které můžete nainstalovat.

5. V seznamu funkcí vyberte **nástroje grafiky** a pak zvolte **nainstalovat**.

   Funkce Graphics Tools je také automaticky nainstalována při instalaci sady Windows 10 SDK.

> [!TIP]
> Volitelná funkce Graphics Tools systému Windows 10 poskytuje funkce prostého zachytávání a přehrávání, jako je například program pro zachycení příkazového řádku **dxcap.exe**, který se dá použít v scénářích podpory, testování a diagnostiky na počítačích, kde nejsou nainstalované vývojářské nástroje. Další informace najdete v tématu [Nástroj pro zachycení z příkazového řádku](../debugger/command-line-capture-tool.md) .

## <a name="using-graphics-diagnostics-for-the-first-time"></a>První použití Diagnostika grafiky
 Teď, když máte všechno, co potřebujete, jste připraveni začít používat Diagnostika grafiky. Postupujte podle těchto kroků.

### <a name="1---create-a-direct3d-app"></a>1. Vytvoření aplikace Direct3D
 Pokud už máte vlastní aplikaci Direct3D, abyste prozkoumali Diagnostika grafiky s, Skvělé! V opačném případě můžete použít jeden z ukázek rozhraní Direct3D dostupných v galerii kódu.

- Pokud si chcete vyzkoušet Diagnostika grafiky s Direct3D 12 ve Windows 10 pomocí sady Visual Studio 2015, vyzkoušejte si [ukázku Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) pro Windows 10.

- K vyzkoušení Diagnostika grafiky s využitím Direct3D 11 ve Windows 10 nebo Windows 8.1 můžete použít šablony projektů **aplikace DirectX (Windows Universal)** nebo  **aplikace DirectX (Windows 8.1)** . Nebo pokud chcete něco zajímavější, vyzkoušejte si [ukázku hry rozhraní DirectX mramor bludiště](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) pro Windows 8.1.

  Ujistěte se, že aplikaci můžete vytvořit před přechodem na.

### <a name="2---start-a-graphics-diagnostics-session"></a>2. spuštění relace Diagnostika grafiky
 Teď jste připraveni začít svoji první relaci diagnostiky grafiky. V aplikaci Visual Studio v hlavní nabídce zvolte možnost **ladění, grafika, spustit diagnostiku**nebo stačí stisknout klávesy **ALT + F5**. Tím se aplikace spustí v rámci Diagnostika grafiky a zobrazí okna diagnostické relace v aplikaci Visual Studio.

> [!IMPORTANT]
> Pokud aplikaci spouštíte ve Windows 10 a ještě nemáte nainstalovanou funkci volitelné grafické nástroje, zobrazí se vám výzva k tomu, abyste to provedli nyní. Než budete moct použít Diagnostika grafiky ve Windows 10, musíte ho nainstalovat.

### <a name="3---capture-frames"></a>3. zachytávání snímků
 Jste připraveni zachytit snímky hned po spuštění aplikace.

##### <a name="to-capture-single-frames"></a>Zachycení jednoho rámce

- V sadě Visual Studio vyberte tlačítko **zachytit snímek** z panelu nástrojů grafiky nebo okna relace diagnostiky. Nebo pokud vaše aplikace má fokus, stačí stisknout **tiskovou obrazovku**.

##### <a name="to-capture-a-sequence-of-frames"></a>Zachycení posloupnosti snímků

- V sadě Visual Studio v okně diagnostická relace nastavte **snímky pro zachycení** na počet snímků, které chcete zachytit v sekvenci, a potom Zachyťte sekvenci pomocí kterékoli z metod, které jste si popsali výše, abyste mohli zachytit jednotlivé snímky.

   Pokud chcete zachytit jeden snímek znovu, nastavte **snímky pro zachycení** `1` .

  Až zachytíte snímky, ukončete aplikaci nebo klikněte na tlačítko **zastavit** z panelu nástrojů grafiky nebo okna relace diagnostiky.

### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4 – Kontrola zachycených snímků v analyzátoru grafiky
 Teď jste připraveni zkontrolovat snímky, které jste právě zachytili. Chcete-li zahájit analýzu snímku, vyberte číslo rámce rámce, který chcete prošetřit z okna diagnostické relace. Tím se otevře rámec v **analyzátoru grafiky**, kde můžete pomocí Diagnostika grafikych nástrojů zjistit, jak vaše aplikace využívá Direct3D ke sledování problémů s vykreslováním, nebo použít nástroj pro **analýzu snímků** k pochopení jeho výkonu.

 Pokud jste vybrali špatný rámec z okna diagnostické relace nebo chcete prošetřit jiný snímek, můžete z analyzátoru grafiky vybrat nový. Na kartě **cíl vykreslování** okna log Graphics v části Obrázek cíle vykreslování rozbalte **seznam rámců** a zvolte jiný rámec, který chcete prošetřit.

 Další informace o tom, jak používat nástroje analyzátoru grafiky společně, najdete v [příkladech](../debugger/graphics-diagnostics-examples.md).

## <a name="see-also"></a>Viz také
 [Technologie Direct3D 12 Graphics](https://msdn.microsoft.com/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)
