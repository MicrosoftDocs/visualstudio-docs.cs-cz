---
title: Principy konfigurací sestavení
description: Tento článek popisuje různé konfigurace sestavení v Sadě Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 0bd35d415a60ea64c479b19cb506c58c2c346cc0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983592"
---
# <a name="understanding-build-configurations"></a>Principy konfigurací sestavení

## <a name="project-build-configurations"></a>Konfigurace sestavení projektu

Projekty mají tendenci mít více konfigurací a přepínání mezi nimi umožňuje různé výstupy v době sestavení. Například konfigurace ladění bude výstup ladicí symboly, což ladicí program přeložit názvy funkcí, parametry nebo proměnné z trasování zásobníku havaroval aplikace. I když tyto další informace jsou užitečné během vývoje, vede k nafouknuté velikosti souboru a není ideální pro distribuci.

Každá platforma má specifické konfigurace pro jeho sestavení.

## <a name="solution-configurations"></a>Konfigurace řešení

Stejně jako konfigurace projektu, konfigurace řešení se používají k vytvoření vlastní konfigurace pro celý projekt. Pomocí karty **Mapování konfigurace** v položce Sestavení > **konfigurace** můžete přiřadit cílovou konfiguraci pro každou položku řešení, jak je znázorněno na následujícím obrázku:

![Možnosti mapování konfigurace](media/projects-and-solutions-image3.png)

Další informace o konfiguracích najdete ve videu [nástroje Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) od Jamese Montemagna.

## <a name="run-configuration"></a>Spustit konfiguraci

V předchozích verzích Xamarin Studio, můžete vybrat možnost nastavit projekt jako **spouštěcí projekt**, což je projekt, který je spuštěn/laděný při použití příkazu global run/debug. To bylo označeno tučným písmem pro název projektu v panelu projektu.

V Sadě Visual Studio for Mac můžete místo nastavení spouštěcího projektu nastavit _konfiguraci spuštění_. Konfigurace spuštění jsou uvedeny v rozevíracím seznamu na panelu nástrojů vedle voliče konfigurace sestavení, jak je znázorněno níže:

![Spustit rozevírací název Konfigurace](media/projects-and-solutions-image8.png)

Konfigurace spuštění je sada možností spuštění s názvem a několika konfiguracemi, které jsou definovány v projektu pro různé účely. Konfigurace spuštění jsou definovány na úrovni projektu a výchozí bude vytvořen automaticky pro každý spustitelný projekt, i když je možné přidat tolik, kolik je potřeba. Některé typy projektů automaticky generují další konfigurace spuštění. Například watchOS projekty mohou generovat _přehled a oznámení konfigurace._

Konfigurace mohou být sdíleny s jinými vývojáři (v takovém případě budou konfigurace uloženy v souboru .csproj) nebo uchovávány místně (v takovém případě budou uloženy v souboru .user).

### <a name="android-run-configurations"></a>Konfigurace spuštění systému Android

Spouštění konfigurací pro projekty Android umožňuje určit, kterou aktivitu, službu nebo přijímač všesměrového vysílání má spustit při spuštění nebo ladění projektu. Můžete předat záměr další data a nastavit příznaky záměru, aby bylo možné testovat komponenty za různých podmínek spuštění.

Jiné aktivity `MainLauncher` než bude `Exported=true` muset mít přidány do Activity atribut pro ladění na fyzické zařízení nebo mají intent filtry definované.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Příklady dat, která mohou být zahrnuta do konfigurace spuštění

Následující seznam obsahuje některé příklady dat, která by mohla být zahrnuta do konfigurace spuštění:

* Pravidelný projekt .NET
  * Alternativní spouštěcí aplikace
  * Počáteční argumenty
  * Pracovní adresář
  * Proměnné prostředí
  * Možnosti mono runtime (pro použití pouze při spuštění na Mono)
* Android projekt
  * Vstupní bod (činnost, služba, příjemce)
  * Argumenty záměru a data
* Projekt iOS
  * Režim (normální, načítání na pozadí)
* Projekt rozšíření iOS
  * Spouštěcí aplikace: výchozí nebo vlastní
* Projekt WatchKit
  * Režim (Pohled, oznámení)
  * Datová část oznámení

## <a name="see-also"></a>Viz také

- [Principy konfigurací sestavení (Visual Studio v systému Windows)](/visualstudio/ide/understanding-build-configurations)
