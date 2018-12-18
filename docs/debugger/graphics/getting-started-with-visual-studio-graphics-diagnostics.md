---
title: Začínáme s diagnostikou grafiky | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 05/26/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 422a0fa4ea44cb3a605b8905282a5fe2a7e71e4c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055462"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Začínáme s diagnostikou grafiky sady Visual Studio
V této části budete připravit k použití diagnostiky grafiky poprvé, pak budete moct zachytit snímků z aplikace Direct3D a kontrole v analyzátoru grafiky.  
  
## <a name="requirements"></a>Požadavky  
 K použití diagnostiky grafiky v aplikaci Visual Studio, musíte použít Visual Studio Enterprise, Visual Studio Professional nebo Visual Studio Community.  Ostatní, včetně edice Visual Studio Code, neobsahují tuto funkci.
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Požadavky na systém Windows 10  
 Volitelná funkce Windows *nástroje grafiky* poskytuje infrastrukturu zachytávání a přehrávání, který vyžaduje diagnostiky grafiky ve Windows 10.  
  
 Informace o instalaci nástrojů grafiky, naleznete v tématu [instalace nástrojů grafiky pro Windows 10](#InstallGraphicsTools).  
  
##  <a name="InstallGraphicsTools"></a> Instalace nástrojů grafiky pro systém Windows 10  
 Ve Windows 10, infrastruktury Diagnostika grafiky poskytuje volitelnou funkcí Windows volá *nástroje grafiky*. Tato funkce se vyžaduje pro zachytávání a přehrávání grafické informace ve Windows 10 bez ohledu na to, jestli aplikace zachytí cíle předchozí verze systému windows nebo používá verze rozhraní Direct3D. Můžete také nainstalovat součást nástroje grafiky předem; v opačném případě bude nainstalovaná na vyžádání první čas spuštění relace diagnostiky grafiky v sadě Visual Studio.  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>Instalace nástrojů grafiky pro Windows 10  
  
1. Do pole hledání zadejte **aplikace a funkce** a pak otevřete **aplikace a funkce** nastavení.
  
2. Na pravé straně **aplikace a funkce** dialogovém okně zvolte **spravovat volitelné funkce** (v části **aplikace a funkce**).

   **Spravovat volitelné funkce** se zobrazí dialogové okno.
  
3. V **spravovat volitelné funkce** dialogovém okně zvolte **přidat funkci**. Zobrazí se seznam volitelných funkcí, které můžete nainstalovat.  
  
4. Vyberte **nástroje grafiky** ze seznamu funkcí, klikněte na tlačítko **nainstalovat**.  
  
   Součást nástroje grafiky je také automaticky nainstalován při instalaci Windows 10 SDK.  
  
> [!TIP]
>  Volitelná součást nástroje grafiky Windows 10 obsahuje jednoduchý záznam a přehrávání funkce – například program příkazového řádku pro zachytávání **dxcap.exe**–, který je možné v podpory, testování a diagnostických scénáře počítače, kde nejsou nainstalovány nástroje pro vývojáře. Další informace najdete v tématu [nástroj příkazového řádku pro zachycení](command-line-capture-tool.md) tématu.  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>Při prvním použití diagnostiky grafiky  
 Teď, když máte všechno, co potřebujete, jste připraveni začít používat diagnostiku grafiky. Postupujte podle těchto kroků.  
  
### <a name="1---create-a-direct3d-app"></a>1 – Vytvoření aplikace Direct3D  
 Pokud už máte vlastní aplikace Direct3D a prozkoumejte diagnostiky grafiky, skvěle! V opačném případě použijte jednu z následujících akcí:

- **Aplikace DirectX 11 (Universal Windows)** nebo **rozhraní DirectX 12 aplikace (Universal Windows)** šablony projektů pro Windows 10.
- [Ukázka Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) pro Windows 10.  
  
  Zajistěte, aby že při vytváření aplikace než budete pokračovat.  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2 - spustit relaci diagnostiky grafiky  
 Teď jste připravení začít s vaší první relace diagnostiky grafiky. V sadě Visual Studio, zvolte v hlavní nabídce **ladění, grafiky, spustit ladění grafiky**, nebo stačí stisknout kombinaci kláves **Alt + F5**. To spustí vaši aplikaci v rámci diagnostiky grafiky a zobrazí okno relace diagnostiky v sadě Visual Studio.  
  
> [!IMPORTANT]
>  Pokud spouštíte aplikaci ve Windows 10 a volitelná součást nástroje grafiky ještě nenainstalovali, budete vyzváni k tomu teď. Musíte jej nainstalovat abyste mohli používat diagnostiky grafiky ve Windows 10.  
  
### <a name="3---capture-frames"></a>3 - zachycování snímků  
 Jste připraveni k zachycení snímků co nejdříve po spuštění vaší aplikace.  
  
#### <a name="to-capture-single-frames"></a>K zachycení snímků jedné  
  
-   V sadě Visual Studio, zvolte **zachytit snímek** tlačítko z okna nástrojů nebo diagnostiky grafiky relace. Nebo, pokud vaše aplikace má fokus, stačí stisknout kombinaci kláves **Print Screen** kláves na klávesnici.
  
#### <a name="to-capture-a-sequence-of-frames"></a>K zachycení sekvence rámce  
  
- V sadě Visual Studio, v okně diagnostické relace nastavit **snímky k zachycení** počet snímků, které chcete zaznamenat v sekvenci, pak zachytíte pořadí pomocí některé z metod popsaných výše pro zachycení jeden snímek.  
  
   Chcete-li zaznamenat jeden snímek znovu, nastavte **snímky k zachycení** k *1*.  
  
  Až to budete mít zachytávání snímků právě ukončete aplikaci, nebo zvolte **Zastavit** tlačítko panelu nástrojů grafiky nebo okno diagnostické relace.  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 – prozkoumejte zachycených snímcích v analyzátoru grafiky  
 Nyní jste připraveni prozkoumat snímky, které jste zachytili. Ke spuštění analýzy blok, zvolte číslo rámce rámce, které chcete prověřit z okna diagnostické relace. Tím se otevře v rámci **analyzátoru grafiky sady**, kde můžete prozkoumat, jak vaše aplikace používá rozhraní Direct3D ke sledování problémů s vykreslováním pomocí nástrojů diagnostiky grafiky, nebo použít **analýza snímků** nástroje jeho výkon.  
  
 Pokud jste vybrali nesprávný rámec v okně diagnostické relace nebo které chcete prověřit jiný snímek můžete vybrat nový štítek z Graphics Analyzeru. Na **cíl vykreslování** kartu protokolu grafickém okně pod obrázkem cíl vykreslování, rozbalte **seznam snímků** a pak zvolte jiný snímek prozkoumat.  
  
 Další informace o tom, jak použít nástroje pro analyzátor grafiky sady společně, najdete v článku [příklady](graphics-diagnostics-examples.md).  
  
## <a name="see-also"></a>Viz také  
 [Direct3D 12 grafiky](/windows/desktop/direct3d12/direct3d-12-graphics)