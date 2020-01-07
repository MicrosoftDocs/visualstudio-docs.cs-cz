---
title: Jak do projektu přidat soubor app.config
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593639"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Postupy: Přidání konfiguračního souboru aplikace k C# projektu

Přidáním konfiguračního souboru aplikace (*app.config* soubor) do C# projektu, jak modul common language runtime vyhledá a načte soubory sestavení můžete přizpůsobit. Další informace o konfiguračních souborech aplikace najdete v tématu [jak běhové prostředí vyhledává sestavení (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> U aplikací pro UPW neobsahují *app.config* souboru.

Při sestavování projektu se automaticky zkopíruje vývojového prostředí vašeho *app.config* souboru, se změní název souboru kopie tak, aby odpovídaly spustitelný soubor a pak přesune kopírovat do **bin** adresář.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Chcete-li přidat do konfiguračního souboru aplikace C# projektu

1. V panelu nabídky zvolte **projektu** > **přidat novou položku**.

     **Přidat novou položku** zobrazí se dialogové okno.

1. Rozbalte **nainstalováno** > **Visual C# položky**a klikněte na tlačítko **konfiguračního souboru aplikace** šablony.

1. V **název** textového pole zadejte název a klikněte na tlačítko **přidat** tlačítko.

     Soubor s názvem *app.config* se přidá do vašeho projektu.

## <a name="see-also"></a>Viz také:

- [Správa nastavení aplikace (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schéma konfiguračního souboru (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurace aplikace (.NET Framework)](/dotnet/framework/configure-apps/index)
