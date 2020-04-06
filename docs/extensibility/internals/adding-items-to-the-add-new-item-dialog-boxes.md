---
title: Přidání položek do dialogových oken Přidat novou položku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7f9e5c792785a23ad1674a50abeb4eb6d3cba9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710215"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Přidání položek do dialogového okna Přidat novou položku
Proces přidávání položek do dialogového okna **Přidat novou položku** začíná klíči registru. Jak je znázorněno v následujících položkách registru, oddíl **AddItemTemplates** obsahuje cestu a název adresáře, do kterého jsou umístěny položky zpřístupněné v dialogovém okně **Přidat novou položku.**

> [!NOTE]
> Tabulka bezprostředně následující za segmentem kódu obsahuje další informace o položce registru.

 Tato část je umístěna pod **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 První identifikátor GUID je identifikátor CLSID pro projekty tohoto typu; druhý identifikátor GUID označuje registrovaný typ projektu pro šablony Přidat položky:

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\AddItemTemplates\\TemplatesDir\\{ACEF4EB2-57CF-11D2-96F4-00000000000}\\1**

 **@**= #6

 **TemplatesDir** = \\&lt;Visual Studio SDK instalační\\&lt;cesta&gt;\\&lt;&gt;\\VSIntegration&gt;\\&lt;SomeFolder SomePackage&gt;\\&lt;SomeProject SomeProjectItems&gt;

 **SortPriority** = dword:00000064

| Name (Název) | Typ | Data (ze souboru *RGS)* | Popis |
|------------------|-----------| - | - |
| @ (Výchozí) | REG_SZ | #%IDS_ADDITEM_TEMPLATES_ENTRY% | ID prostředku pro přidání šablon **položek.** |
| Val TemplatesDir | REG_SZ | %TEMPLATE_PATH%\\&lt;Některé položky projektu&gt; | Cesta k položkám projektu zobrazeným v dialogovém okně průvodce **Přidání nové položky** |
| Val SortPriority | REG_DWORD | 100[!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]( ) | Určuje pořadí řazení souborů zobrazených v dialogovém okně **Přidat novou položku** v uzlu stromu. |

> [!NOTE]
> Guids pro typy projektů Visual C# a Visual Basic jsou následující:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 Adresář uvedený pro **TemplatesDir**, což je *\\&lt;%TEMPLATE_PATH% SomeProjectItems&gt;*, je uzel na levé straně stromu dialogového okna Přidat novou **položku.** Další prvky ve stromu jsou založeny na podadresáři v tomto kořenovém adresáři. Soubory, které jsou k dispozici k přidání do projektu, jsou položky v pravém podokně dialogového okna **Přidat novou položku.**

 Tato složka obvykle obsahuje soubory šablon pro váš projekt, například soubor ŠABLONY HTML nebo *CPP,* a všechny soubory *VSZ* pro spuštění průvodců. Chcete-li určit způsob zobrazení položek, můžete také zahrnout soubory *.vsdir* pro lokalizaci názvů adresářů a ikon. Lokalizovaný řetězec je titulek, který se zobrazí v dialogovém okně, které představuje tento uzel ve stromu dialogového okna **Přidat novou položku.**

 Však není třeba mít vše v jednom souboru *.vsdir.* Můžete mít jeden soubor *VSDIR* pro každou položku v adresáři. Další informace naleznete v [tématu Průvodce (.vsz) soubor](../../extensibility/internals/wizard-dot-vsz-file.md) a [popis adresáře šablony (.vsdir) soubory](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

> [!NOTE]
> Soubory *.vsdir* v adresářích šablon jsou volitelné. Pokud chcete pouze vložit prvek projektu do adresáře a zobrazit jej v dialogovém okně **Přidat novou položku,** můžete tento soubor umístit do adresáře šablon určeného v příkazu **TemplatesDir.** Soubor se pak zobrazí v pravém podokně dialogového okna **Přidat novou položku** pro tento projekt. Pokud však chcete zobrazit lokalizovaný titulek pro soubor nebo ikonu, musíte do adresáře šablon zahrnout alespoň jeden soubor *VSDIR.*

## <a name="group-project-items"></a>Seskupit položky projektu
 Pokud chcete obsahovat skupiny šablon ve složkách ve stromu dialogového okna **Přidat novou položku,** musíte mít podadresáře pod kořenovou šablonou pod adresářem kořenové šablony s položkami v nich. Když se uživatelům zobrazí dialogové okno **Přidat novou položku,** uvidí také podsložky a budou z nich moci vybírat prvky projektu.

 Priorita řazení v segmentu kódu určuje, kde bude tento adresář šablony vytvořen ve stromu vzhledem k ostatním prvkům uzlu stromu. V dialogovém okně **Přidat novou položku** je prioritou řazení vše, co je nutné zahrnout, aby se položky v dialogovém okně zobrazily ve správném umístění.

 Můžete také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> rozhraní pro filtrování toho, co je zobrazeno v dialogovém okně Přidat novou **položku.** Implementací tohoto rozhraní můžete nastavit jeden adresář šablony na disku, který obsahuje například 50 souborů šablon a průvodců. Tímto způsobem můžete mít různé typy projektů s 20 soubory, které patří do jednoho typu projektu, dalších 30 souborů, které patří do jiného typu projektu a všechny soubory, které jsou k dispozici v obecném typu projektu. Tímto způsobem v závislosti na vytvoření šablony projektu můžete zobrazit jinou sadu souborů šablon.

 Například v projektu jazyka Visual Basic můžete mít webové projekty a klientské projekty. Webové formuláře nejsou užitečné položky přidat do klientského projektu a formuláře systému Windows nejsou užitečné položky přidat do projektu webového serveru. Proto můžete vytvořit jeden adresář šablony, který obsahuje všechny soubory pro oba typy projektu. Implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>potom můžete skrýt položky, které by neměly být zobrazeny na základě typu projektu nebo nastavení projektu v projektu.

## <a name="filter-project-items"></a>Filtrování položek projektu
 `IVsFilterAddProjectItemDlg2`poskytuje filtrování prvků ve stromu (levé podokno) a soubory projektu (pravé podokno) následujícími způsoby:

- Podle lokalizovaných názvů (titulky zobrazené v dialogovém okně obsaženém v souboru `IVsFilterAddProjectItemDlg` *.vsdir)* poskytovaném společností .

- Podle skutečných názvů souborů a složek na disku (nelokalizované – žádný `IVsFilterAddProjectItemDlg` *soubor VSDIR)* poskytované programem .

- Podle kategorie, poskytované `IVsFilterAddProjectItemDlg2`.

  Chcete-li filtrovat podle kategorií, zadejte řetězec kategorie pro položku v souboru *.vsdir,* například *webový formulář* nebo *položku Klient* v jazyce Visual Basic. Kód dialogového okna pak načte klasifikaci kategorií ze souboru *.vsdir* a předá vám ji. Tyto informace pak můžete předat `IVsFilterAddProjectItemDlg2` implementaci aplikace a filtrovat dialogové okno **Přidat novou položku** podle kategorií. Můžete také filtrovat položky pro webové stránky nebo jako klient win32 případy aplikace. Kromě toho můžete [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] identifikovat označené položky jako položky Třídy Microsoft Foundation (MFC) nebo aktivní knihovny šablon (ATL). Při identifikaci těchto položek může systém projektu definovat vlastní klasifikace tak, aby systém mohl být filtrován na základě kategorií a klasifikací.

  Pokud implementujete tuto funkci filtru, není třeba mapovat tabulku každé položky, která by měla být skryta. Položky můžete jednoduše klasifikovat do typů a umístit klasifikace do souboru *.vsdir* nebo souborů. Potom můžete skrýt všechny položky, které mají konkrétní klasifikaci implementací rozhraní. Tímto způsobem můžete položky v dialogovém okně **Přidat novou položku** dynamické na základě stavu v rámci projektu.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [CATID pro objekty, které se obvykle používají k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Přidání šablon položek projektu a projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Soubory popisu adresáře šablony (.vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Soubor Průvodce (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
