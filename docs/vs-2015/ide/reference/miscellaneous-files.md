---
title: Různé soubory | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dc11714fc8b2d5a345d94ddfe4c5de2c2cd7fe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666848"
---
# <a name="miscellaneous-files"></a>Ostatní soubory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Můžete chtít použít [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editory pro práci nezávisle na souborech z projektu nebo řešení. Když máte otevřené řešení, můžete otevřít a upravit soubory bez jejich přidání do řešení nebo projektu. Soubory, se kterými chcete pracovat nezávisle na kontejnerech, se nazývají různé soubory. Různé soubory jsou externí pro řešení a projekty, nejsou zahrnuty v sestaveních a nelze je zahrnout do řešení pod správou zdrojových kódů.

 Otevírání souborů nezávisle na kontejneru je užitečné z nejrůznějších důvodů. Je možné, že máte soubor, který chcete zobrazit během vývoje řešení založeného na projektu, ale není integrální pro vývoj řešení. Mezi běžné příklady patří poznámky k vývoji nebo pokyny, schéma databáze a klipy kódu. Kromě toho může být vhodné vytvořit samostatný soubor.

 ![Projekty řešení](../../ide/reference/media/projects-solutions-misc.gif "Projects_Solutions_Misc")

 Průzkumník řešení může pro soubory zobrazit různé soubory, pokud jsou povolené možnosti složky. Možnosti lze nastavit v [dialogu dokumenty, prostředí, možnosti](../../ide/reference/documents-environment-options-dialog-box.md). Po zavření různých souborů není přidružena k žádnému konkrétnímu řešení nebo projektu, pokud není povolena možnost i.

 Složka různé soubory představuje soubory jako odkazy. I když tato složka není součástí řešení, když otevřete řešení, některé nebo všechny různé soubory, které byly otevřeny při poslední uzávěrce řešení, budou znovu otevřeny v závislosti na nastavení složky.

> [!NOTE]
> Některé soubory, které se nezobrazují ve složce různé soubory, jsou soubory, které nelze upravovat v rámci integrovaného vývojového prostředí (IDE), jako jsou soubory. zip a soubory. doc. Rozhraní IDE nebude sledovat soubory, které lze upravovat pouze pomocí externího editoru.

## <a name="commands-available-in-the-ide"></a>Příkazy dostupné v integrovaném vývojovém prostředí
 Nabídky, panely nástrojů a příkazy, které obsahují změny, jsou založeny na formátu souboru, který jste otevřeli. Když otevřete textový soubor, zobrazí se například panel nástrojů textový editor a jeho příkazy jsou k dispozici. Pokud pak otevřete soubor schématu XML, zobrazí se panel nástrojů schématu XML. Při úpravách schématu XML nejsou příkazy panelu nástrojů textový editor (nebo samotného panelu nástrojů) k dispozici. Schéma XML je aktivní okno a jako takové má aktuální kontext výběru. Když přepínáte mezi souborem projektu a různými soubory, všechny příkazy související s projektem zmizí a zobrazí se pouze ty, které se přímo vztahují k různým souborům.

## <a name="folder-display-options"></a>Možnosti zobrazení složky
 Můžete nastavit možnosti zobrazení pro složku různé, aby se složka zobrazila, i když jste neotevřeli žádné jiné soubory. Soubor řešení trvale nespravuje seznam různých souborů. Používá volitelnou funkci, která umožňuje zapamatovat si seznam souborů naposledy použitých (naposledy použitých) pro jednotlivé uživatele.

## <a name="see-also"></a>Viz také
 [Dokumenty, prostředí, dialogové okno Možnosti](../../ide/reference/documents-environment-options-dialog-box.md) [a projekty řešení](../../ide/solutions-and-projects-in-visual-studio.md)
