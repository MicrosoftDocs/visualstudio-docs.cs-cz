---
title: Jak přidat soubor App. config do projektu
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 48e6516b48b524c3da4d80bc5171608ac1aea03d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654265"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Postupy: Přidání konfiguračního souboru aplikace do C# projektu

Přidáním konfiguračního souboru aplikace (soubor*App. config* ) do C# projektu můžete přizpůsobit, jak modul CLR (Common Language Runtime) hledá a načte soubory sestavení. Další informace o konfiguračních souborech aplikace naleznete v tématu [jak modul runtime vyhledává sestavení (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Aplikace UWP neobsahují soubor *App. config* .

Při sestavování projektu vývojové prostředí automaticky zkopíruje soubor *App. config* , změní název souboru kopie tak, aby odpovídal vašemu spustitelnému souboru, a pak přesune kopii do adresáře **bin** .

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Přidání konfiguračního souboru aplikace do C# projektu

1. Na panelu nabídek vyberte možnost **projekt**  > **Přidat novou položku**.

     Zobrazí se dialogové okno **Přidat novou položku** .

1. Rozbalte položku **nainstalované**  > **vizuální C# položky**a pak zvolte šablonu **konfigurační soubor aplikace** .

1. Do textového pole **název** zadejte název a pak klikněte na tlačítko **Přidat** .

     Do projektu se přidá soubor s názvem *App. config* .

## <a name="see-also"></a>Viz také:

- [Správa nastavení aplikace (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schéma konfiguračního souboru (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurace aplikací (.NET Framework)](/dotnet/framework/configure-apps/index)