---
title: Dia2dump – ukázka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/24/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2e44abdce737df335133d5e54b6b022c97f639a
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252278"
---
# <a name="dia2dump-sample"></a>Dia2dump – ukázka

Dia2dump – ukázka ukazuje, jak použít k dotazování soubor PDB pro informace o Microsoft ladění rozhraní přístup Software Development Kit (DIA SDK).

Dia2dump – ukázka je součástí sady Visual Studio a obsahuje řešení a zdrojových souborech. Kompilovaný spustitelný soubor se spustí z příkazového řádku. Může zobrazit obsah souboru databáze (PDB) celého programu, nebo pouze oddíly vás zajímá.

## <a name="install-the-sample"></a>Ukázku nainstalujete

Ukázka se nainstaluje, když zvolíte **vývoj desktopových aplikací pomocí C++** úlohy v instalačním programu sady Visual Studio. Informace o tom, jak nainstalovat sadu Visual Studio a zvolte konkrétní úlohy a jednotlivé komponenty najdete v tématu [instalace sady Visual Studio](../../install/install-visual-studio.md).

Při instalaci, vzorek je v adresáři instalace sady Visual Studio v podadresáři s názvem \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Vytvoření vzorku

Ve výchozím nastavení je v instalačním adresáři chráněném adresáři. To znamená, že musí použít příkazový řádek se zvýšenými oprávněními pro vývojáře nebo instanci sady Visual Studio vytvářet a upravovat ukázkové řešení v tomto umístění. Pro zjednodušení sestavení, doporučujeme nejprve zkopírovat soubory z ukázkové adresáře do jiného adresáře, jako je například složka ve složce Dokumenty a potom sestavit ukázku.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>K vytvoření dia2dump – ukázka v sadě Visual Studio

1. Otevřete soubor DIA2Dump.sln v sadě Visual Studio. Pokud řešení není nezkopírovali do jiného adresáře, vám může zobrazit výzva k restartování sady Visual Studio se zvýšenými oprávněními.

1. V **Průzkumníka řešení**, vyberte projekt dia2dump – (nikoli řešení).

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](/cpp/ide/working-with-project-properties).

1. Otevřít **vlastnosti konfigurace** > **C/C++** > **Obecné** stránku vlastností.

1. V **další adresáře souborů k zahrnutí** vlastnost, zvolte ovládací prvek rozevírací seznam a zvolte **upravit**.

1. V **další adresáře souborů k zahrnutí** dialogové okno Upravit pole, zadejte `$(VSInstallDir)DIA SDK\include` adresáře. Přidejte tento adresář zaručí, že kompilátor dokáže najít soubor dia2.h. Zvolte **OK** uložte provedené změny.

1. Zvolte **OK** uložte provedené změny ve vlastnostech projektu.

1. Na **sestavení** nabídce zvolte **znovu sestavit řešení**. Visual Studio ve výchozím nastavení, sestavení ladicí verze ukázky, které jsou umístěny v podadresáři ladění adresáře řešení.

1. Zavřete Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>K vytvoření dia2dump – ukázka příkazového řádku

1. V okně příkazového řádku pro vývojáře přejděte do adresáře, kam jste zkopírovali ukázkové soubory. Pokud vzorek nezkopírovali do jiného adresáře, je nutné použít s rozšířenými oprávněními (Spustit jako správce) okno příkazového řádku pro vývojáře.

1. Zadejte příkaz `nmake makefile` vytvářet konfigurace ladění výchozí dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Spustit dia2dump – ukázka

Dia2Dump.exe se může spolehnout msdia*verze*server DLL modelu COM pro poskytování jeho služeb. V sadě Visual Studio 2015 a Visual Studio 2017 verze je knihovnu msdia140.dll. Pokud msdia*verze*server DLL modelu COM není inicializován, je třeba jej zaregistrovat před dia2dump.exe můžete pracovat. Adresář sady DIA SDK má bin podadresář, který obsahuje x86 verzi knihovny DLL. Verze pro x64 architektura počítače je v bin\amd64 a verze pro ARM je v bin\arm. Zaregistruje knihovnu dll, otevřete okno příkazového řádku pro vývojáře se zvýšenými oprávněními a přejděte do adresáře, který obsahuje verzi pro architekturu vašeho počítače. Zadejte příkaz `regsvr32 msdia140.dll` registrace modelu COM serveru.

### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

1. Otevřete příkazový řádek a přejděte do adresáře, který obsahuje dia2dump.exe, kterou jste vytvořili.

1. Zadejte příkaz `dia2dump filename` kde *filename* je název souboru PDB a zkoumat. Pokud soubor PDB je v jiném adresáři, použít úplnou cestu k souboru jako *filename*. Tento příkaz vypíše všechna data v souboru PDB.

1. Dia2dump – obsahuje další možnosti zobrazíte pouze vybrané informace. Použití `dia2dump -?` příkazu zobrazte výpis všech dostupných možností.

## <a name="see-also"></a>Viz také:

- [Přenos, migrace a Upgrade projektů sady Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)  
