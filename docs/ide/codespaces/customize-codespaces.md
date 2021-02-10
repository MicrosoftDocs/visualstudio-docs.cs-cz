---
title: Přizpůsobení codespace (Preview)
description: Přečtěte si další informace o tom, jak přizpůsobit codespace.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 15efee817e41f928e5ca1162e9ace20276bd20d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971151"
---
# <a name="how-to-customize-a-codespace-preview"></a>Přizpůsobení codespace (Preview)

GitHub Codespaces poskytuje plnohodnotné vývojové prostředí v cloudu. V případě vývoje založeného na systému Windows pomocí sady Visual Studio 2019 výchozí instance služby GitHub Codespaces poskytují skvělý počáteční bod, ale můžete také přizpůsobit prostředí pro konkrétní projekt.

## <a name="installed-software"></a>Nainstalovaný software

Windows codespaces už má nainstalovanou spoustu rozhraní a nástrojů, abyste mohli začít hned. V následující tabulce jsou uvedené aplikace a funkce, které jsou dostupné ve všech prostředích Windows codespace.

| Aplikace                                         | Alias cesty | Verze            |
|---------------------------------------------|------------|--------------------|
| .NET                                        | –        | 4.8                |
| .NET Core Runtime                           | dotnet     | 2,1, 3,1           |
| Sada .NET Core SDK                               | dotnet     | 2,1, 3.1.3, 3.1.4  |
| Azure CLI                                   | AZ         | 2.5                |
| Chocolatey                                  | choco      | 0.10.15            |
| CMake                                       | cmake      | 3,17               |
| Git                                         | git        | 2,26               |
| Microsoft Build                             | nástroji    | 16,7               |
| Microsoft SQL Server Express edice 2019   | –        | 15,0               |
| Expertem                                       | expertem      | 1.8.2              |
| Node.js                                     | node       | 12,16              |
| NPM                                         | npm        | 6,14               |
| Python                                      | python     | 3.7                |
| Správce balíčků VC                          | vcpkg      | 2020,02            |
| Sada SDK pro Windows                                 | –        | 10.0.18362         |

Výše uvedený seznam není vyčerpávající a vylučuje mnoho nástrojů, které Visual Studio nainstaluje (například IISExpress). Komponenta může mít také jinou dílčí nebo opravnou verzi než ta, která je uvedena výše.

Konkrétní podrobnosti o předinstalovaných architekturách a nástrojích najdete níže v části [nainstalované konkrétní software](#installed-software-specifics) .

## <a name="modifications-to-a-codespace"></a>Úpravy codespace
 
Po vytvoření codespace budou všechny změny v těchto konkrétních codespace trvalé, zatímco instance codespace je k dispozici na GitHubu Codespaces. Můžete klonovat další úložiště, instalovat nástroje a generátory aplikací a přidávat další prostředky pro vývoj a tyto úpravy se zachovají i v případě, že je codespace pozastaven. Pokud však odstraníte codespace, všechny úpravy budou ztraceny.

> [!NOTE]
> Pokud codespace odstraníte, ztratí se všechny změny v místním úložišti (čekající nebo potvrzené) v codespace. Před odstraněním codespace nezapomeňte vložit změny úložiště do vzdáleného umístění.

I když jste připojeni k codespace pomocí sady Visual Studio, můžete použít terminál sady Visual Studio pro spouštění nástrojů příkazového řádku. V rámci místního účtu správce můžete použít buď PowerShell, nebo příkazový řádek systému Windows. Další informace o terminálu sady Visual Studio najdete na blogu o [oznámení terminálu pro Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/).

## <a name="customize-a-codespace"></a>Přizpůsobení codespace

Skutečná hodnota GitHubu Codespaces přichází v případě, že můžete vytvořit jedinečná a opakující se vývojová prostředí v cloudu, která jsou přizpůsobená vaší vlastní práci i vašemu týmu. Vytvořením výchozí instance Codespaces GitHubu můžete přizpůsobit, co se má nainstalovat a nakonfigurovat při vytváření nového codespace.

Následující části popisují dvě metody konfigurace codespace, které používají *.devcontainer.jsv* a *.devinit.jsna* souborech. Tyto soubory umožňují nakonfigurovat instalační architektury a nástroje pro codespace a přidané do úložiště, takže každý, kdo vytvoří codespace na základě vašeho úložiště, bude mít stejné vzdálené vývojové prostředí.

## <a name="customize-with-devcontainerjson"></a>Přizpůsobení pomocí devcontainer.js

Když se vytvoří codespace, GitHub Codespaces vyhledá [*devcontainers.js*](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) v souboru v kořenovém adresáři vašeho úložiště a použije nastavení v rámci k přizpůsobení codespace nebo instancí klienta, které se k němu připojují (prohlížeč – základní editor, Visual Studio nebo Visual Studio Code). Většina *devcontainer.jsv* nastavení se vztahuje na codespaces se systémem Linux nebo na dva ostatní klienty, ale některé jsou k dispozici pro systémy Windows Codespaces a Visual Studio.

*devcontainer.jsv* souboru lze umístit do jednoho ze dvou míst v úložišti:

1. *{úložiště-root}/.devcontainer.jszapnuto*
2. *{úložiště-root}/.devcontainer/devcontainer.jsdne*

Codespaces GitHubu podporuje na vlastnostech následující *devcontainer.js* . Nastavení specifických vlastností Visual Studio Code je užitečné, pokud očekáváte, že se připojíte ke svému codespace spolu s ostatními klienty kromě sady Visual Studio. 

* `extensions` – Pole Visual Studio Code rozšíření [Marketplace](https://marketplace.visualstudio.com/vscode) , která by se měla nainstalovat.
* `settings`  – Sada [nastavení Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) , která se mají použít.
* `forwardPorts`– Port nebo pole portů, které by měly být automaticky předány místně, když je spuštěný codespace.
* `postCreateCommand` – Řetězec příkazu nebo seznam argumentů příkazu, které mají být spuštěny po vytvoření codespace.

> [!NOTE]
> **devcontainer.js** se soubory používají také k podpoře [vzdáleného vývoje](https://code.visualstudio.com/docs/remote/remote-overview)Visual Studio Code a další vlastnosti, které nejsou zahrnuty v tomto dokumentu. Tyto další vlastnosti jsou bezpečné pro přidání do souboru, ale budou Codespaces ignorovat. Další informace najdete v tématu [devcontainer.jsv článku referenční informace](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) o Code.VisualStudio.com.

## <a name="customize-with-devinit"></a>Přizpůsobení pomocí devinit

[devinit](../../devinit/getting-started-with-devinit.md) je nástroj příkazového řádku, který je součástí Windows codespaces, který umožňuje do svého prostředí nainstalovat rozhraní a nástroje. Dá se spustit ručně z příkazového řádku ( `devinit run -t require-dotnetcoresdk` ), ale jeho skutečný výkon pochází z vytvoření vlastního [ *.devinit.jsv*](../../devinit/devinit-json.md) souboru pro jednotnou konfiguraci codespace, kdykoli ho vytvoříte.

`devinit` obsahuje sadu nástrojů pro instalaci konkrétních položek, jako je SQL Server a Azure CLI, a také spuštění obecných správců balíčků, jako jsou čokolády, npm a vcpkg. Úplný seznam `devinit` nástrojů najdete v dokumentaci [k dostupným nástrojům](../../devinit/devinit-tool-list.md) .

### <a name="devinitjson"></a>devinit.jsna

I když můžete `devinit` příkazový řádek spustit přímo, doporučujeme vytvořit [*devinit.jsv*](../../devinit/devinit-json.md) konfiguračních souborech, které popisují sadu nástrojů, které `devinit` se mají spustit. 

Chcete-li například nainstalovat [.NET Core SDK](/dotnet/core/sdk), *.devinit.js* by vypadalo takto:

```json
{
    "run": [
        {
            "comments": "We need the .NET Core SDK."
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

Při vytváření *.devinit.js* v souboru v kořenovém adresáři projektu, bude použit při spuštění `devinit init` . Ve výchozím nastavení `devinit.exe` vyhledá soubor v následujících umístěních:

1. *{Current-Directory} \\.devinit.jsna*
2. *{Current-Directory} \\.devinit\devinit.jsna*

### <a name="running-devinit-when-creating-a-codespace"></a>Spuštění devinit při vytváření codespace

Můžete nastavit, aby se na GitHubu Codespaces spouštěla `devinit` po vytvoření codespace pomocí `postCreateCommand` vlastnosti v souboru *devcontainers.js* . Jak je uvedeno výše, GitHub Codespaces bude hledat *devcontainer.js* v souboru v klonovaném úložišti, aby bylo možné přizpůsobit codespace nebo instanci klienta, a spustí všechny příkazy popsané ve `postCreateCommand` Vlastnosti.

Když zadáte, spustí se `devinit init` `devinit` v konfiguraci pomocí *devinit.js* .

```json
{
  "postCreateCommand": "devinit init"
}
```

### <a name="an-example"></a>Příklad

Tady je jednoduchý příklad instalace nástroje příkazového řádku .NET Core Entity Framework `dotnet-ef` .

**devcontainer.json**

Obsah *.devcontainer.js* v souboru v kořenovém adresáři úložiště. 

```json
{
  "postCreateCommand": "devinit init"
}
```

**devinit.jsna**

Obsah *.devinit.jsv* souboru. Tento soubor musí být ve stejné složce jako *.devcontainer.jsna*.

```json
{
    "run": [
        {
            "comments": "Install the Entity Framework tools",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
        }
     ]
}
```

Další `devinit` Příklady najdete v `devinit` [seznamu ukázek](../../devinit/sample-readme.md).

## <a name="port-forwarding"></a>Přesměrování portů

GitHub Codespaces poskytuje přístup k aplikacím a službám běžícím ve vzdáleném prostředí prostřednictvím předávání portů. Ve výchozím nastavení nejsou předávány žádné porty z důvodu zabezpečení. Můžete ale zadat určité porty, které se otevřou v codespace.

### <a name="configure-port-forwarding"></a>Konfigurace přesměrování portů

Pokud je k dispozici jeden nebo více portů, které by měly být ve výchozím nastavení předávány pro dané úložiště, které lze konfigurovat v *devcontainer.js* s `forwardPorts` vlastností.

* `forwardPorts` – Port nebo pole portů, které by měly být automaticky předávány místně, když prostředí běží.

## <a name="installed-software-specifics"></a>Nainstalované konkrétní software

### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Edice Microsoft SQL Server 2019 Express je dostupná a spuštěná jako místní služba (LocalDB) v prostředí Windows Codespace. Aktuální uživatel, na kterém běží aplikace a terminál sady Visual Studio, má práva správce SQL k SQL serveru. Pokud chcete server spravovat, budete muset použít PowerShell v terminálu sady Visual Studio nebo v jiných nástrojích příkazového řádku, jako je `dotnet-ef` . Aktuálně SQL Server Management Studio a další nástroje pro vzdálenou správu nejsou k dispozici.

#### <a name="example-connection-string"></a>Příklad připojovacího řetězce

Níže je příklad připojovacího řetězce pro připojení k místnímu systému MS SQL Server.

```csharp
"Server=(LocalDB);Integrated Security=true;"
```

### <a name="azure-cli"></a>Azure CLI

Rozhraní příkazového řádku Azure je nainstalované ve všech prostředích Windows Codespace a je k dispozici na cestě jako `az` .

#### <a name="using-azure-resources"></a>Používání prostředků Azure

Pokud používáte identitu Azure Active Directory k ověření vaší aplikace proti prostředkům Azure, musíte se nejdřív přihlásit k Azure z terminálu Visual studia. Pokud se chcete přihlásit, použijte příkaz Azure CLI `login` s tokem přihlášení zařízení (jak je znázorněno v následujícím příkladu). Po přihlášení by vaše aplikace a relace terminálu měly být schopné použít tuto identitu.

```powershell
> az login --use-device-code
```

Další informace najdete v dokumentaci k `az login` rozhraní příkazového řádku Azure [](/cli/azure/reference-index#az_login)CLI.

## <a name="see-also"></a>Viz také

- [Co je GitHub Codespaces?](codespaces-overview.md)
- [Jak používat Visual Studio s codespace](use-visual-studio-with-codespaces.md)