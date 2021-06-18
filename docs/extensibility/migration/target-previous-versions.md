---
title: Cíl sady Visual Studio 2019 při vytváření rozšíření v aplikaci Visual Studio 2022 Preview
description: Naučte se, jak pomocí sady Visual Studio 2019 pracovat s rozšířením sady Visual Studio, pokud vytvoříte projekt pomocí sady Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: dcf556e271e6a805110eac0c978a845f2195e28f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308758"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-preview"></a>Cíl předchozí verze při vytváření rozšíření v aplikaci Visual Studio 2022 Preview

[!INCLUDE [preview-note](../includes/preview-note.md)]

Když vytvoříte nový projekt VSIX pomocí sady Visual Studio 2022 Preview, projekt se vytvoří ze šablony, která se zaměřuje na Visual Studio 2022. Chcete-li cílit na verzi sady Visual Studio 2019 nebo starší, je nutné upravit vytvořený projekt.

Zvažte použití [sdílených projektů](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) pro cílení na sady visual Studio 2019 a visual Studio 2022 při sdílení většiny nebo veškerého kódu v rozšíření.

Postupujte podle těchto kroků v projektu VSIX, který by měl cílit na Visual Studio 2019:

1. Upravte `source.extension.vsixmanifest` soubor tak, aby se odstranil `ProductArchitecture` element a rozsah verze:

    ```diff
    -<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
    +<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[16.0,17.0)">
    -  <ProductArchitecture>amd64</ProductArchitecture>
     </InstallationTarget>
    ```

   Aktualizujte taky požadavek:

    ```diff
    -<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,18.0)" DisplayName="Visual Studio core editor" />
    +<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[16.0,17.0)" DisplayName="Visual Studio core editor" />
    ```

    Zkontrolujte soubor pro všechny další aktualizace, které mohou být nezbytné.

1. Změňte verze balíčků sady VS SDK, na které odkazujete v souboru projektu:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    ```
