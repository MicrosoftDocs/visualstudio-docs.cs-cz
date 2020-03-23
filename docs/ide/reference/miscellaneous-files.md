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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585294"
---
# <a name="miscellaneous-files"></a>Ostatní soubory

Můžete chtít použít editor sady Visual Studio pracovat na souborech nezávisle na projektu nebo řešení. I když máte otevřené řešení, můžete otevřít a upravit soubory bez jejich přidání do řešení nebo do projektu. Soubory, se kterými chcete pracovat nezávisle, se nazývají různé soubory. Různé soubory jsou externí řešení a projekty, nejsou zahrnuty v sestavení a nemohou být zahrnuty s řešením pod správou zdrojového kódu.

Otevírání souborů nezávisle na projektu nebo řešení je užitečné z různých důvodů. Můžete mít soubor, který chcete zobrazit při vývoji řešení založeného na projektu, ale to není nedílnou součástí vývoje řešení. Mezi běžné příklady patří vývojové poznámky nebo pokyny, schéma databáze a klipy kódu. Kromě toho můžete chtít vytvořit samostatný soubor.

![Projekty řešení](../../ide/reference/media/projects_solutions_misc.gif)

Průzkumník řešení může zobrazit složku Různé soubory pro soubory, pokud jsou **povoleny** možnosti pro složku. Možnosti lze nastavit v [dialogovém okně Dokumenty, Prostředí, Možnosti](../../ide/reference/documents-environment-options-dialog-box.md). Po zavření různého souboru není přidružen k žádnému konkrétnímu řešení nebo projektu, pokud není povolena možnost.

Složka **Různé soubory** představuje soubory jako odkazy. Přestože tato složka není součástí řešení, při otevření řešení, některé nebo všechny různé soubory, které byly otevřeny při posledním uzavření řešení jsou znovu otevřeny, v závislosti na nastavení pro složku.

> [!NOTE]
> Některé soubory, které se nezobrazují ve složce **Různé soubory,** jsou soubory, které nelze v rámci ide upravit, například soubory ZIP a soubory .doc. Rozhraní IDE nesleduje soubory, které lze upravit pouze prostřednictvím externího editoru.

## <a name="commands-available-in-the-ide"></a>Příkazy dostupné v rozhraní IDE

Nabídky, panely nástrojů a příkazy, které obsahují, se mění na základě formátu souboru, který otevřete. Když například otevřete textový soubor, zobrazí se například panel nástrojů Editor textu a jeho příkazy jsou k dispozici. Pokud potom otevřete soubor schématu XML, zobrazí se panel nástrojů schéma XML. Při úpravách schématu XML nejsou příkazy panelu nástrojů textového editoru (nebo samotného panelu nástrojů) k dispozici. Schéma XML je aktivní okno a jako takové má aktuální kontext výběru. Když přepnete mezi souborem projektu a různého souboru, zmizí všechny příkazy související s projektem a zobrazí se pouze ty, které přímo souvisejí s vedlejším souborem.

## <a name="folder-display-options"></a>Možnosti zobrazení složky

Můžete nastavit možnosti zobrazení pro složku Různé soubory tak, aby se složka **zobrazila,** i když jste neotevřeli žádné různé soubory. Soubor řešení trvale nespravuje seznam různých souborů. Používá volitelnou funkci, která mu umožňuje zapamatovat si seznam souborů pro jednotlivé uživatele, naposledy použitý (MRU).

## <a name="see-also"></a>Viz také

- [Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Řešení a projekty](../../ide/solutions-and-projects-in-visual-studio.md)
- [Dokumenty, prostředí, dialogové okno Možnosti](../../ide/reference/documents-environment-options-dialog-box.md)
