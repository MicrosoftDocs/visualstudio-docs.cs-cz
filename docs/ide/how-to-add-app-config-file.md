---
title: Jak přidat soubor app.config do projektu
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3eb813dc5d4389b002851a904d61219b0d5c316e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593639"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Postup: Přidání konfiguračního souboru aplikace do projektu jazyka C#

Přidáním konfiguračního souboru aplikace (soubor*app.config)* do projektu Jazyka C# můžete přizpůsobit způsob, jakým běžný jazyk runtime vyhledá a načte soubory sestavení. Další informace o konfiguračních souborech aplikací naleznete [v tématu Jak runtime vyhledá sestavení (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Aplikace UPW neobsahují soubor *app.config.*

Při vytváření projektu vývojové prostředí automaticky zkopíruje soubor *app.config,* změní název souboru kopie tak, aby odpovídal spustitelnému souboru, a pak ji přesune do **adresáře přihrádky.**

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Přidání konfiguračního souboru aplikace do projektu jazyka C#

1. Na řádku nabídek zvolte Přidat**novou položku** **projektu** > .

     Zobrazí se dialogové okno **Přidat novou položku**.

1. Rozbalte **nainstalované** > **položky Visual C#** a pak zvolte šablonu **Konfigurační soubor aplikace.**

1. Do textového pole **Název** zadejte název a pak zvolte tlačítko **Přidat.**

     Do projektu je přidán soubor s názvem *app.config.*

## <a name="see-also"></a>Viz také

- [Správa nastavení aplikace (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schéma konfiguračního souboru (rozhraní.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurace aplikací (rozhraní.NET Framework)](/dotnet/framework/configure-apps/index)
