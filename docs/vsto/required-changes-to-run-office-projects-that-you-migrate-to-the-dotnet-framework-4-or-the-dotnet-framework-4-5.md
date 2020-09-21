---
title: Změny požadované pro projekty Office migrované na .NET Framework 4, 4,5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 773a4dd319d00487b919721bf3390a7d58c8b03c
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810964"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Požadované změny pro spouštění projektů Office, které migrujete do .NET Framework 4 nebo .NET Framework 4,5
  Pokud se cílová architektura projektu Office změní na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější z dřívější verze .NET Framework, musíte provést následující úlohy, abyste zajistili, že řešení může běžet na vývojovém počítači a na počítačích koncových uživatelů:

- <xref:System.Security.SecurityTransparentAttribute>Pokud jste provedli upgrade ze sady Visual Studio 2008, odeberte z projektu.

- Proveďte příkaz **vyčistit** v aplikaci Visual Studio, aby bylo možné spustit nebo ladit projekt ve vývojovém počítači.

- Aktualizujte předpoklad .NET Framework pro projekt.

- Koncoví uživatelé musí přeinstalovat řešení i v případě, že jste ho předtím nasadili pomocí technologie ClickOnce předtím, než jste změnili cílovou architekturu.

  Další informace o jednotlivých úlohách najdete v odpovídajících částech níže.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Odebrání atributu atributy SecurityTransparent z projektů, které upgradujete ze sady Visual Studio 2008
 Pokud upgradujete projekt Office ze sady Visual Studio 2008 a cílová architektura projektu následně změníme na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, musíte <xref:System.Security.SecurityTransparentAttribute> z projektu odebrat. Visual Studio tento atribut automaticky neodstraní. Pokud tento atribut neodstraníte, při kompilování projektu se zobrazí chybová zpráva.

 Další informace o podmínkách, ve kterých může Visual Studio změnit cílovou architekturu upgradovaného projektu na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , najdete v tématu [upgrade a migrace řešení pro systém Office](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>Postup odebrání atributu SecurityTransparentAttribute

1. S projektem otevřeným v aplikaci Visual Studio otevřete **Průzkumník řešení**.

2. V uzlu **Properties** (pro C#) nebo v uzlu **můj projekt** (pro Visual Basic) poklikejte na soubor kódu AssemblyInfo a otevře se v editoru kódu.

    > [!NOTE]
    > V Visual Basic projektů musíte kliknutím na tlačítko **Zobrazit všechny soubory** v **Průzkumník řešení** zobrazit soubor kódu AssemblyInfo.

3. Vyhledejte <xref:System.Security.SecurityTransparentAttribute> soubor a buď ho odeberte ze souboru, nebo ho Odkomentujte.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Provedení příkazu vyčistit pro ladění nebo spuštění projektu ve vývojovém počítači
 Pokud byl projekt sady Office vytvořen před změnou cílové architektury projektu na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, musíte provést příkaz **vyčistit** a po změně cílového rozhraní znovu sestavit projekt. Pokud příkaz **vyčistit** neprovedete, zobrazí se <xref:System.Runtime.InteropServices.COMException> při pokusu o ladění nebo spuštění přecíleného projektu.

 Další informace o příkazu **vyčistit** najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Aktualizace požadavků pro nasazení
 Při změny cílení projektu sady Office na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější je nutné v dialogovém okně **předpoklady** aktualizovat také odpovídající požadavek .NET Framework. V opačném případě projekt ClickOnce Deployment nebo InstallShield Limited Edition zkontroluje a nainstaluje předchozí verzi .NET Framework.

 Další informace o aktualizaci požadavků pro nasazení na počítače koncových uživatelů najdete v tématu [Postup: instalace požadavků na počítače koncových uživatelů ke spouštění řešení pro systém Office](/previous-versions/bb608608(v=vs.110)).

## <a name="reinstall-solutions-on-end-user-computers"></a>Přeinstalujte řešení na počítačích koncových uživatelů.
 Použijete-li ClickOnce k nasazení řešení pro systém Office, které cílí na .NET Framework 3,5 a potom změníte cíl projektu na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později, musí koncový uživatel řešení odinstalovat a po opětovném publikování pak řešení znovu nainstalovat. Pokud znovu publikujete řešení cíle a řešení je aktualizováno na počítačích koncových uživatelů, budou koncoví uživatelé dostávat <xref:System.Runtime.InteropServices.COMException> při spuštění aktualizovaného řešení.

## <a name="see-also"></a>Viz také
- [Migrace řešení Office na .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)