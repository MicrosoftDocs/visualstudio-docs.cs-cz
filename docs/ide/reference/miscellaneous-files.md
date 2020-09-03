---
title: Ostatní soubory
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], miscellaneous
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793500faf217c74772506b4b7394d926447ffd40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585294"
---
# <a name="miscellaneous-files"></a>Ostatní soubory

Můžete chtít použít Editor sady Visual Studio pro práci se soubory nezávisle na projektu nebo řešení. Když máte otevřené řešení, můžete otevřít a upravit soubory bez jejich přidání do řešení nebo projektu. Soubory, se kterými chcete pracovat nezávisle, se nazývají různé soubory. Různé soubory jsou externí pro řešení a projekty, nejsou zahrnuty v sestaveních a nelze je zahrnout do řešení pod správou zdrojových kódů.

Otevírání souborů nezávisle na projektu nebo řešení je užitečné z nejrůznějších důvodů. Je možné, že máte soubor, který chcete zobrazit během vývoje řešení založeného na projektu, ale není integrální pro vývoj řešení. Mezi běžné příklady patří poznámky k vývoji nebo pokyny, schéma databáze a klipy kódu. Kromě toho může být vhodné vytvořit samostatný soubor.

![Projekty řešení](../../ide/reference/media/projects_solutions_misc.gif)

Průzkumník řešení může pro soubory zobrazit **různé soubory** , pokud jsou povolené možnosti složky. Možnosti lze nastavit v [dialogu dokumenty, prostředí, možnosti](../../ide/reference/documents-environment-options-dialog-box.md). Po zavření různých souborů není přidružena k žádnému konkrétnímu řešení nebo projektu, pokud není povolena možnost i.

Složka **různé soubory** představuje soubory jako odkazy. I když tato složka není součástí řešení, po otevření řešení se znovu otevřou některé nebo všechny různé soubory, které byly otevřeny při poslední uzávěrce řešení, v závislosti na nastavení složky.

> [!NOTE]
> Některé soubory, které se nezobrazují ve složce **různé soubory** , jsou soubory, které nelze upravovat v rámci integrovaného vývojového prostředí (IDE), jako jsou soubory. zip a soubory. doc. Rozhraní IDE nesleduje soubory, které lze upravovat pouze pomocí externího editoru.

## <a name="commands-available-in-the-ide"></a>Příkazy dostupné v integrovaném vývojovém prostředí

Nabídky, panely nástrojů a příkazy, které obsahují změny, jsou založeny na formátu souboru, který jste otevřeli. Když otevřete textový soubor, zobrazí se například panel nástrojů textový editor a jeho příkazy jsou k dispozici. Pokud pak otevřete soubor schématu XML, zobrazí se panel nástrojů schématu XML. Při úpravách schématu XML nejsou příkazy panelu nástrojů textový editor (nebo samotného panelu nástrojů) k dispozici. Schéma XML je aktivní okno a jako takové má aktuální kontext výběru. Když přepínáte mezi souborem projektu a různými soubory, všechny příkazy související s projektem zmizí a zobrazí se pouze ty, které se přímo vztahují k různým souborům.

## <a name="folder-display-options"></a>Možnosti zobrazení složky

Můžete nastavit možnosti zobrazení pro složku **různé soubory** tak, aby se složka zobrazila, i když jste neotevřeli žádné jiné soubory. Soubor řešení trvale nespravuje seznam různých souborů. Používá volitelnou funkci, která umožňuje, aby si pamatovala na uživatele, naposledy použitý seznam souborů.

## <a name="see-also"></a>Viz také

- [Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Řešení a projekty](../../ide/solutions-and-projects-in-visual-studio.md)
- [Dokumenty, prostředí, dialogové okno Možnosti](../../ide/reference/documents-environment-options-dialog-box.md)
