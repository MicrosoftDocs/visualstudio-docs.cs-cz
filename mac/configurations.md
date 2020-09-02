---
title: Principy konfigurací sestavení
description: Tento článek popisuje různé konfigurace sestavení v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "71128402"
---
# <a name="understanding-build-configurations"></a>Principy konfigurací sestavení

Můžete ukládat různé konfigurace vlastností řešení a projektu pro použití v různých typech sestavení během procesu vývoje. Projekty vytvořené pomocí Visual Studio pro Mac, které používají šablonu, budou obvykle zahrnovat konfigurace ladění a vydání, které podporují ladění aplikace a nasazení aplikace v uvedeném pořadí. 

Chcete-li vytvořit vlastní konfigurace, přečtěte si téma [vytváření a úpravy konfigurací sestavení](/visualstudio/mac/create-and-edit-configurations).

>[!NOTE]
>Toto téma se týká Visual Studio pro Mac. Informace o aplikaci Visual Studio ve Windows najdete v tématu [Principy konfigurací sestavení](/visualstudio/ide/understanding-build-configurations).

## <a name="solution-configurations"></a>Konfigurace řešení

Konfigurace řešení se používají k určení konfigurací pro všechny projekty v řešení. Pomocí karty **mapování konfigurace** pod položkou **Konfigurace > sestavení** můžete přiřadit cílovou konfiguraci pro každou položku v otevřeném řešení. To je znázorněno na následujícím obrázku:

![Možnosti mapování konfigurace](media/projects-and-solutions-image3.png)

Další informace o konfiguracích najdete v tématu [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) video od James Montemagno.

## <a name="project-build-configurations"></a>Konfigurace sestavení projektu

Projekty mají více konfigurací. Konfigurace a platforma: cíle projektu se společně používají k určení vlastností, které se použijí při sestavení. Přepínání mezi konfiguracemi umožňuje různé výstupy v době sestavení. Například konfigurace ladění bude výstupem symbolů ladění, což umožňuje ladicímu programu překládat názvy, parametry a proměnné funkcí z chybných trasování zásobníku aplikace. I když jsou tyto další informace užitečné během vývoje, vede k neploché velikosti souborů a nejsou ideální pro distribuci.

Každá platforma má specifické konfigurace pro sestavení. Stránky konfigurace sestavení pro projekty mohou být k dispozici, když přejdete na část **sestavení** v dialogovém okně **Možnosti projektu** . Otevřete toto dialogové okno tak, že kliknete pravým tlačítkem na projekt a vyberete **Možnosti** nebo dvakrát kliknete na projekt v Průzkumníku řešení.

## <a name="run-configuration"></a>Konfigurace spuštění

Visual Studio pro Mac umožňuje nastavit _konfiguraci spuštění_. Konfigurace spuštění jsou uvedeny v rozevíracím seznamu na panelu nástrojů vedle selektoru konfigurace sestavení, jak je znázorněno níže:

![Rozevírací seznam konfigurace spuštění](media/projects-and-solutions-image8.png)

Konfigurace spuštění je sada možností spuštění s názvem a několika konfiguracemi, které jsou definovány v projektu pro různé účely. Konfigurace spuštění jsou definovány na úrovni projektu a výchozí nastavení se vytvoří automaticky pro každý spustitelný projekt, i když je možné přidat tolik, kolik potřebujete. Některé typy projektů automaticky generují další konfigurace spuštění. Například projekty watchOS mohou generovat  _přehledy a konfigurace oznámení._

Konfigurace je možné sdílet s jinými vývojáři (v takovém případě se konfigurace uloží v souboru. csproj) nebo v místním prostředí (v takovém případě budou uloženy v souboru. User).

### <a name="android-run-configurations"></a>Konfigurace spuštění Androidu

Konfigurace spuštění pro projekty v systému Android umožňují zadání konkrétní aktivity, služby nebo přijímače všesměrového vysílání, které se spustí při spuštění nebo ladění projektu. Můžete předat dodatečné data a nastavit příznaky záměru k otestování komponent v rámci různých podmínek spuštění.

Jiné aktivity než musí `MainLauncher` být `Exported=true` přidány do atributu Activity pro ladění na fyzickém zařízení nebo mají definovány filtry záměrů.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Příklady dat, která mohou být součástí konfigurací spuštění

Následující seznam obsahuje příklady dat, která mohou být součástí konfigurací spuštění:

* Běžný projekt .NET
  * Alternativní úvodní aplikace
  * Počáteční argumenty
  * Pracovní adresář
  * Proměnné prostředí
  * Možnosti Mono runtime (budou použity pouze při spuštění na mono)
* Projekt pro Android
  * Vstupní bod (aktivita, služba, přijímač)
  * Argumenty záměru a data
* projekt iOS
  * Režim (normální, načítání na pozadí)
* projekt rozšíření pro iOS
  * Aplikace po spuštění: výchozí nebo vlastní
* Projekt WatchKit
  * Režim (stručný přehled, oznámení)
  * Datová část oznámení

## <a name="see-also"></a>Viz také

- [Principy konfigurací sestavení (Visual Studio ve Windows)](/visualstudio/ide/understanding-build-configurations)
