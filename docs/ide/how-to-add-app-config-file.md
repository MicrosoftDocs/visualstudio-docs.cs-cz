---
title: Postup přidání souboru app.config do projektu
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe659979cadf4d9e5752f7bbe85150aae848de08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770823"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Postupy: Přidání konfiguračního souboru aplikace do projektu C#

Přidáním konfiguračního souboru aplikace (*app.config* souboru) do projektu C# můžete přizpůsobit, jak modul CLR (Common Language Runtime) vyhledá a načte soubory sestavení. Další informace o konfiguračních souborech aplikace naleznete v tématu [jak modul runtime vyhledává sestavení (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Aplikace UWP neobsahují soubor *app.config* .

Při sestavování projektu vývojové prostředí automaticky zkopíruje soubor *app.config* , změní název souboru kopie tak, aby odpovídal vašemu spustitelnému souboru, a pak přesune kopii do adresáře **bin** .

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Přidání konfiguračního souboru aplikace do projektu C#

1. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

     Zobrazí se dialogové okno **Přidat novou položku**.

1. Rozbalte položku **nainstalované**  >  **položky Visual C#** a pak zvolte šablonu **konfigurační soubor aplikace** .

1. Do textového pole **název** zadejte název a pak klikněte na tlačítko **Přidat** .

     Do projektu se přidá soubor s názvem *app.config* .

## <a name="see-also"></a>Viz také

- [Správa nastavení aplikace (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schéma konfiguračního souboru (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurace aplikací (.NET Framework)](/dotnet/framework/configure-apps/index)
