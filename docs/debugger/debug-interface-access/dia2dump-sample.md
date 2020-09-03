---
title: Ukázka Dia2dump – | Microsoft Docs
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17fe6d65e70399ccac5b9ef4e2f1234ef4e3698e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468684"
---
# <a name="dia2dump-sample"></a>Dia2dump – ukázka

Ukázka Dia2dump – ukazuje, jak použít sadu Microsoft Debug Interface Access Software Development Kit (DIA SDK) k dotazování souboru PDB na informace.

Ukázka Dia2dump – je nainstalována se sadou Visual Studio a obsahuje řešení a zdrojové soubory. Kompilovaný spustitelný soubor se spouští z příkazového řádku. Může zobrazit obsah celého souboru databáze programu (PDB) nebo jenom oddíly, které vás zajímají.

## <a name="install-the-sample"></a>Instalace ukázky

Tato ukázka se nainstaluje, když v Instalační program pro Visual Studio zvolíte **vývoj desktopových aplikací s C++** . Informace o tom, jak nainstalovat sadu Visual Studio a zvolit konkrétní úlohy a jednotlivé komponenty, najdete v tématu [instalace sady Visual Studio](../../install/install-visual-studio.md).

Při instalaci se ukázka nachází v adresáři pro instalaci sady Visual Studio v podadresáři s názvem \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Sestavení ukázky

Ve výchozím nastavení je instalační adresář chráněný adresářem. To znamená, že k sestavení a úpravě ukázkového řešení v tomto umístění musíte použít příkazový řádek nebo instanci sady Visual Studio se zvýšenými oprávněními. Pro zjednodušení sestavení doporučujeme nejprve zkopírovat soubory z ukázkového adresáře do jiného adresáře, jako je například složka ve složce Dokumenty, a potom sestavit ukázku.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Sestavení ukázky Dia2dump – v aplikaci Visual Studio

1. V aplikaci Visual Studio otevřete soubor Dia2dump –. sln. Pokud jste řešení nezkopírovali do jiného adresáře, může se zobrazit výzva k restartování sady Visual Studio se zvýšenými oprávněními.

1. V **Průzkumník řešení**vyberte projekt Dia2dump – (ne řešení).

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti naleznete v tématu [práce s vlastnostmi projektu](/cpp/build/working-with-project-properties).

1. Otevřete stránku **vlastností**  >  Obecné vlastnost konfigurace**C/C++**  >  **General** .

1. Ve vlastnosti **Další adresáře pro zahrnutí** zvolte ovládací prvek rozevírací seznam a pak zvolte možnost **Upravit**.

1. V dialogovém okně **Další adresáře k zahrnutí** zadejte do pole upravit `$(VSInstallDir)DIA SDK\include` adresář. Přidejte tento adresář, aby bylo zaručeno, že kompilátor může najít soubor Dia2. h. Kliknutím na **tlačítko OK** uložte změny.

1. Kliknutím na **tlačítko OK** uložte změny vlastností projektu.

1. V nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**. Ve výchozím nastavení Visual Studio vytvoří ladicí verzi ukázky, která se nachází v podadresáři ladění adresáře řešení.

1. Zavřete Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Sestavení ukázky Dia2dump – na příkazovém řádku

1. V okně příkazového řádku pro vývojáře přejděte do adresáře, kam jste zkopírovali ukázkové soubory. Pokud jste ukázku nezkopírovali do jiného adresáře, musíte použít okno příkazového řádku pro vývojáře se zvýšenými oprávněními (Spustit jako správce).

1. Zadejte příkaz `nmake makefile` pro sestavení výchozí konfigurace ladění dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Spuštění ukázky Dia2dump –

Dia2Dump.exe spoléhá na server s rozhraním COM MSDIA*verze*. dll, aby poskytoval své služby. Počínaje verzí Visual Studio 2015 je verze msdia140.dll. Pokud není inicializován Server MSDIA*verze*. dll modelu COM, je nutné jej zaregistrovat, aby mohla aplikace dia2dump.exe fungovat. Adresář DIA SDK obsahuje podadresář bin, který obsahuje verzi x86 knihovny DLL. Verze pro počítače s architekturou x64 je v bin\amd64 a verze pro ARM je v bin\arm.. Pokud chcete knihovnu DLL zaregistrovat, otevřete okno příkazového řádku pro vývojáře se zvýšenými oprávněními a přejděte do adresáře, který obsahuje verzi vaší architektury počítače. Zadejte příkaz `regsvr32 msdia140.dll` pro registraci serveru com.

### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

1. Otevřete příkazový řádek a přejděte do adresáře, který obsahuje dia2dump.exe, který jste vytvořili.

1. Zadejte příkaz `dia2dump filename` , kde *filename* je název souboru PDB k prohlédnutí. Pokud je soubor PDB v jiném adresáři, použijte úplnou cestu k souboru jako *název*souboru. Tento příkaz vypíše všechna data v souboru PDB.

1. Dia2dump – má další možnosti, jak zobrazit pouze vybrané informace. Pomocí `dia2dump -?` příkazu můžete zobrazit seznam všech dostupných možností.

## <a name="see-also"></a>Viz také

- [Port, migrace a upgrade projektů sady Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
