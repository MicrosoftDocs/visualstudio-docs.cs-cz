---
title: Přidávání položek do dialogových oken Přidat novou položku | Microsoft Docs
description: Naučte se, jak přidat položky do dialogového okna Přidat novou položku v aplikaci Visual Studio, abyste mohli zobrazit šablony a prvky projektu pro použití ve vašich projektech.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 70bc1a0c4d90d8cab0b2193550773745fc2dd47e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904406"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Přidání položek do dialogového okna Přidat novou položku
Proces přidávání položek do dialogového okna **Přidat novou položku** začíná klíči registru. Jak je znázorněno v následujících položkách registru, část **AddItemTemplates** obsahuje cestu a název adresáře, ve kterém jsou položky zpřístupněny v dialogovém okně **Přidat novou položku** .

> [!NOTE]
> Tabulka hned následující po segmentu kódu obsahuje další informace o položce registru.

 Tato část je umístěná v části **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 První identifikátor GUID je identifikátor CLSID pro projekty tohoto typu; Druhý identifikátor GUID označuje typ registrovaného projektu pro šablony přidat položky:

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\ AddItemTemplates \\ TemplatesDir \\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \\ 1**

 **@** = #6

   =  \\ TemplatesDir &lt; Instalační cesta k sadě Visual Studio SDK &gt; \\ VSIntegration \\ &lt; SomeFolder &gt; \\ &lt; SomePackage &gt; \\ &lt; SomeProject &gt; \\ &lt; SomeProjectItems&gt;

 **SortPriority** = DWORD: 00000064

| Název | Typ | Data (ze souboru *. rgs* ) | Description |
|------------------|-----------| - | - |
| @ (Výchozí) | REG_SZ | #% IDS_ADDITEM_TEMPLATES_ENTRY% | ID prostředku pro šablony pro **Přidání položek** |
| Val TemplatesDir | REG_SZ | % TEMPLATE_PATH% \\ &lt; SomeProjectItems&gt; | Cesta k položkám projektu zobrazeným v dialogovém okně průvodce **přidáním nové položky** |
| Val SortPriority | REG_DWORD | 100 ( [!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)] ) | Určuje pořadí řazení v uzlu stromu souborů zobrazených v dialogovém okně **Přidat novou položku** . |

> [!NOTE]
> Identifikátory GUID pro typy projektů jazyka Visual C# a Visual Basic jsou následující:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 Adresář uvedený pro **TemplatesDir**, který je *% TEMPLATE_PATH% \\ &lt; SomeProjectItems &gt;*, je uzel na levé straně stromu dialogového okna **Přidat novou položku** . Další prvky ve stromu jsou založeny na podadresáři v daném kořenovém adresáři. Soubory, které jsou k dispozici pro přidání do projektu, jsou položky v pravém podokně dialogového okna **Přidat novou položku** .

 Obvykle tato složka bude obsahovat soubory šablon pro váš projekt, jako je například šablona HTML nebo *. cpp* , a všechny soubory *. vsz* pro spouštění průvodců. Chcete-li určit, jak se položky zobrazí, můžete také zahrnout soubory *. vsdir* pro lokalizaci názvů a ikon adresářů. Lokalizovaný řetězec je titulek, který se zobrazí v dialogovém okně, které představuje tento uzel ve stromové struktuře dialogového okna **Přidat novou položku** .

 Nemusíte ale mít všechno v jednom souboru *. vsdir* . Pro každou položku v adresáři můžete mít jeden soubor *. vsdir* . Další informace najdete v tématech [soubor průvodce (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) a [Popis adresáře šablon (. vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

> [!NOTE]
> Soubory *. vsdir* v adresářích šablon jsou nepovinné. Pokud chcete pouze vložit prvek projektu do adresáře a zobrazit ho v dialogovém okně **Přidat novou položku** , můžete tento soubor umístit do adresáře šablon zadaného v příkazu **TemplatesDir** . Soubor se pak zobrazí v pravém podokně dialogového okna **Přidat novou položku** pro daný projekt. Pokud ale chcete zobrazit lokalizovaný titulek souboru nebo ikony, musíte do adresáře Templates zahrnout alespoň jeden soubor *. vsdir* .

## <a name="group-project-items"></a>Seskupit položky projektu
 Chcete-li ve složkách ve stromu dialogového okna **Přidat novou položku** obsahovat skupiny šablon, je nutné mít v kořenovém adresáři šablony podadresáře s položkami v nich. Po zobrazení dialogového okna **Přidat novou položku** uživatelům se zobrazí také podsložky a budou moci vybrat prvky projektu z nich.

 Priorita řazení v segmentu kódu určuje, kde bude tento adresář šablon vytvořen ve stromu relativně k ostatním prvkům uzlu stromu. V dialogovém okně **Přidat novou položku** je priorita řazení ta, která musí být zahrnuta, aby se vaše položky zobrazovaly ve správném umístění v dialogovém okně.

 Můžete také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> rozhraní pro filtrování, co se zobrazí v dialogovém okně **Přidat novou položku** . Implementací tohoto rozhraní můžete nastavit jeden adresář šablon na disku, který obsahuje například soubory šablon a souborů Průvodce 50. Tímto způsobem můžete mít různé typy projektů s 20 soubory, které patří do jednoho typu projektu, ostatní 30 souborů, které patří do jiného typu projektu, a všechny soubory, které jsou k dispozici v obecném typu projektu. Tímto způsobem můžete v závislosti na tom, která šablona projektu je vytvořena, zobrazit jinou sadu šablon souborů.

 Například v projektu Visual Basic mohou být webové projekty a klientské projekty. Webové formuláře nejsou užitečnou položkou pro přidání do projektu klienta a formuláře Windows Forms nejsou vhodné pro přidání do projektu webového serveru. Proto můžete vytvořit jeden adresář šablon, který obsahuje všechny soubory pro oba typy projektu. Poté, když implementujete <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> , můžete skrýt položky, které by se neměly zobrazovat v závislosti na typu projektu nebo nastavení projektu v projektu.

## <a name="filter-project-items"></a>Filtrovat položky projektu
 `IVsFilterAddProjectItemDlg2` poskytuje pro filtrování prvků ve stromové struktuře (levé podokno) a soubory projektu (pravé podokno) následujícími způsoby:

- Pomocí lokalizovaných názvů (Titulek zobrazený v dialogovém okně, které je obsaženo v souboru *. vsdir* ), který poskytuje `IVsFilterAddProjectItemDlg` .

- Skutečnými názvy souborů a složek na disku (nelokalizovaný soubor *. vsdir* ), které poskytuje `IVsFilterAddProjectItemDlg` .

- Podle kategorie, kterou poskytuje `IVsFilterAddProjectItemDlg2` .

  Chcete-li filtrovat podle kategorie, zadejte řetězec kategorie pro položku v souboru *. vsdir* , jako je například *webový formulář* nebo *položka klienta* v Visual Basic. Kód dialogového okna pak načte klasifikaci kategorie ze souboru *. vsdir* a předá ji. Tyto informace pak můžete předat do implementace `IVsFilterAddProjectItemDlg2` pro k filtrování dialogového okna **Přidat novou položku** podle kategorií. Můžete také filtrovat položky pro webové stránky nebo jako klientské případy aplikace Win32. Kromě toho můžete identifikovat [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] označené položky jako položky knihovny MFC (Microsoft Foundation Classes) nebo knihovny ATL (Active Template Library). Pokud identifikujete tyto položky, systém projektu může definovat vlastní klasifikace, aby se systém mohl filtrovat na základě kategorií a klasifikací.

  Pokud tuto funkci filtru implementujete, nemusíte mapovat tabulku všech položek, které by měly být skryté. Můžete jednoduše klasifikovat položky do typů a vkládat klasifikace do souboru *. vsdir* nebo soubory. Pak můžete skrýt libovolnou položku, která má konkrétní klasifikaci, implementací rozhraní. Tímto způsobem můžete položky v dialogovém okně **Přidat novou položku** nastavit jako dynamické na základě stavu v rámci projektu.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [CATID pro objekty, které se obvykle používají pro rozšiřování projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Přidat šablony projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Soubory popisu adresáře šablon (. vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Soubor průvodce (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
