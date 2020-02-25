---
title: Začínáme s diagnostikou grafiky | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 05/26/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 575b0254768ac359e43cd5b04c23a220549ac973
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557927"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Začínáme s diagnostikou grafiky sady Visual Studio
V této části budete připravit k použití diagnostiky grafiky poprvé, pak budete moct zachytit snímků z aplikace Direct3D a kontrole v analyzátoru grafiky.

## <a name="requirements"></a>Požadavky
 K použití diagnostiky grafiky v aplikaci Visual Studio, musíte použít Visual Studio Enterprise, Visual Studio Professional nebo Visual Studio Community.  Ostatní, včetně edice Visual Studio Code, neobsahují tuto funkci.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Požadavky na systém Windows 10
 Volitelné *nástroje grafiky* funkcí Windows poskytují infrastrukturu zachytávání a přehrávání, kterou vyžaduje Diagnostika grafiky ve Windows 10.

 Informace o instalaci nástrojů grafiky najdete v tématu [Instalace nástrojů grafiky pro Windows 10](#InstallGraphicsTools).

## <a name="InstallGraphicsTools"></a>Instalace nástrojů grafiky pro Windows 10
 Ve Windows 10 je infrastruktura Diagnostika grafiky poskytovaná volitelnou funkcí Windows s názvem *Graphics Tools*. Tato funkce se vyžaduje pro zachytávání a přehrávání grafické informace ve Windows 10 bez ohledu na to, jestli aplikace zachytí cíle předchozí verze systému windows nebo používá verze rozhraní Direct3D. Můžete také nainstalovat součást nástroje grafiky předem; v opačném případě bude nainstalovaná na vyžádání první čas spuštění relace diagnostiky grafiky v sadě Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Instalace nástrojů grafiky pro Windows 10

1. Do pole Hledat zadejte **aplikace a funkce** a pak otevřete nastavení **aplikace & funkce** .

2. Na pravé straně okna **aplikace & funkce** vyberte možnosti **volitelné funkce** (v části **aplikace & funkce**).

   Zobrazí se nastavení **volitelné funkce** .

3. V nastavení **volitelné funkce** vyberte možnost **Přidat funkci**. Zobrazí se seznam volitelných funkcí, které můžete nainstalovat.

4. V seznamu funkcí vyberte **nástroje grafiky** a pak zvolte **nainstalovat**.

   Součást nástroje grafiky je také automaticky nainstalován při instalaci Windows 10 SDK.

> [!TIP]
> Volitelná funkce Graphics Tools systému Windows 10 poskytuje funkce prostého zachytávání a přehrávání, jako je třeba program pro zachycení příkazového řádku **DXCap. exe**, který se dá použít v scénářích podpory, testování a diagnostiky na počítačích, kde nejsou nainstalované vývojářské nástroje. Další informace najdete v tématu [Nástroj pro zachycení z příkazového řádku](command-line-capture-tool.md) .

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Při prvním použití diagnostiky grafiky
 Teď, když máte všechno, co potřebujete, jste připraveni začít používat diagnostiku grafiky. Postupujte podle těchto kroků.

### <a name="1---create-a-direct3d-app"></a>1 – Vytvoření aplikace Direct3D
 Pokud už máte vlastní aplikace Direct3D a prozkoumejte diagnostiky grafiky, skvěle! V opačném případě použijte jednu z následujících akcí:

- Šablony projektů aplikace **DirectX 11 (univerzální pro Windows)** nebo **aplikace DirectX 12 (univerzální pro Windows)** pro Windows 10.
- [Ukázka Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) pro Windows 10

  Zajistěte, aby že při vytváření aplikace než budete pokračovat.

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - spustit relaci diagnostiky grafiky
 Teď jste připravení začít s vaší první relace diagnostiky grafiky. V aplikaci Visual Studio v hlavní nabídce zvolte možnost **ladění, grafika, spustit ladění grafiky**nebo stačí stisknout klávesy **ALT + F5**. To spustí vaši aplikaci v rámci diagnostiky grafiky a zobrazí okno relace diagnostiky v sadě Visual Studio.

> [!IMPORTANT]
> Pokud spouštíte aplikaci ve Windows 10 a volitelná součást nástroje grafiky ještě nenainstalovali, budete vyzváni k tomu teď. Musíte jej nainstalovat abyste mohli používat diagnostiky grafiky ve Windows 10.

### <a name="3---capture-frames"></a>3 - zachycování snímků
 Jste připraveni k zachycení snímků co nejdříve po spuštění vaší aplikace.

#### <a name="to-capture-single-frames"></a>K zachycení snímků jedné

- V sadě Visual Studio vyberte tlačítko **zachytit snímek** z panelu nástrojů grafiky nebo okna relace diagnostiky. Nebo pokud má vaše aplikace fokus, stačí stisknout na klávesnici klávesu **Print Screen** .

#### <a name="to-capture-a-sequence-of-frames"></a>K zachycení sekvence rámce

- V sadě Visual Studio v okně diagnostická relace nastavte **snímky pro zachycení** na počet snímků, které chcete zachytit v sekvenci, a potom Zachyťte sekvenci pomocí kterékoli z metod, které jste si popsali výše, abyste mohli zachytit jednotlivé snímky.

   Pokud chcete zachytit jeden snímek znovu, nastavte **snímky pro zachycení** na *1*.

  Až zachytíte snímky, ukončete aplikaci nebo klikněte na tlačítko **zastavit** z panelu nástrojů grafiky nebo okna relace diagnostiky.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 – prozkoumejte zachycených snímcích v analyzátoru grafiky
 Nyní jste připraveni prozkoumat snímky, které jste zachytili. Ke spuštění analýzy blok, zvolte číslo rámce rámce, které chcete prověřit z okna diagnostické relace. Tím se otevře rámec v **analyzátoru grafiky**, kde můžete pomocí Diagnostika grafikych nástrojů zjistit, jak vaše aplikace využívá Direct3D ke sledování problémů s vykreslováním, nebo použít nástroj pro **analýzu snímků** k pochopení jeho výkonu.

 Pokud jste vybrali nesprávný rámec v okně diagnostické relace nebo které chcete prověřit jiný snímek můžete vybrat nový štítek z Graphics Analyzeru. Na kartě **cíl vykreslování** okna log Graphics v části Obrázek cíle vykreslování rozbalte **seznam rámců** a zvolte jiný rámec, který chcete prošetřit.

 Další informace o tom, jak používat nástroje analyzátoru grafiky společně, najdete v [příkladech](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Viz také
- [Technologie Direct3D 12 Graphics](/windows/desktop/direct3d12/direct3d-12-graphics)