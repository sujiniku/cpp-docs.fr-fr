# [Génération de programmes C/C++](building-c-cpp-programs.md)
# [Génération d’applications isolées et d’assemblys côte à côte C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
## [Concepts d’applications isolées et d’assemblys côte à côte](concepts-of-isolated-applications-and-side-by-side-assemblies.md)
## [Génération d’applications isolées C/C++](building-c-cpp-isolated-applications.md)
## [Génération d’assemblys côte à côte C/C++](building-c-cpp-side-by-side-assemblies.md)
## [Guide pratique pour générer des composants COM sans inscription](how-to-build-registration-free-com-components.md)
## [Guide pratique pour générer des applications isolées pour consommer des composants COM](how-to-build-isolated-applications-to-consume-com-components.md)
## [Présentation de la génération de manifeste pour les programmes C/C++](understanding-manifest-generation-for-c-cpp-programs.md)
### [Génération de manifeste dans Visual Studio](manifest-generation-in-visual-studio.md)
### [Génération de manifeste au niveau de la ligne de commande](manifest-generation-at-the-command-line.md)
### [Guide pratique pour incorporer un manifeste à une application C/C++](how-to-embed-a-manifest-inside-a-c-cpp-application.md)
## [Dépannage d’applications isolées et d’assemblys côte à côte C/C++](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
# [Configurer Visual C++ pour des cibles x64 64 bits](configuring-programs-for-64-bit-visual-cpp.md)
## [Guide pratique pour configurer des projets Visual C++ pour cibler des plateformes x64 64 bits](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)
## [Guide pratique pour activer un ensemble d’outils du compilateur Visual C++ 64 bits sur la ligne de commande](how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)
## [Problèmes courants de migration vers Visual C++ 64 bits](common-visual-cpp-64-bit-migration-issues.md)
## [Conventions des logiciels x64](x64-software-conventions.md)
### [Vue d’ensemble des conventions d’appel x64](overview-of-x64-calling-conventions.md)
### [Types et stockage](types-and-storage.md)
#### [Types scalaires](scalar-types.md)
#### [Agrégats et unions](aggregates-and-unions.md)
#### [Exemples d’alignement de structure](examples-of-structure-alignment.md)
#### [Champs de bits](bitfields.md)
#### [Conflits avec le compilateur x86](conflicts-with-the-x86-compiler.md)
### [Utilisation des Registres](register-usage.md)
### [Convention d’appel](calling-convention.md)
#### [Passage de paramètres](parameter-passing.md)
#### [Varargs](varargs.md)
#### [Fonctions non prototypées](unprototyped-functions.md)
#### [Valeurs de retour (C++)](return-values-cpp.md)
#### [Registres enregistrés des appelants-appelés](caller-callee-saved-registers.md)
#### [Pointeurs fonction](function-pointers.md)
#### [Prise en charge de la virgule flottante pour le code plus ancien (Visual C++)](floating-point-support-for-older-code-visual-cpp.md)
#### [FpCsr](fpcsr.md)
#### [MxCsr](mxcsr.md)
#### [setjmp-longjump](setjmp-longjump.md)
### [Utilisation de la pile](stack-usage.md)
#### [Allocation de piles](stack-allocation.md)
#### [Construction dynamique d’une zone pour la pile de paramètres](dynamic-parameter-stack-area-construction.md)
#### [Types de fonctions](function-types.md)
#### [Alignement avec malloc](malloc-alignment.md)
#### [alloca](alloca.md)
### [Prologue et épilogue](prolog-and-epilog.md)
### [Gestion des exceptions (x64)](exception-handling-x64.md)
#### [Données de déroulement pour la gestion des exceptions et la prise en charge du débogueur](unwind-data-for-exception-handling-debugger-support.md)
##### [RUNTIME_FUNCTION, struct](struct-runtime-function.md)
##### [UNWIND_INFO, struct](struct-unwind-info.md)
##### [UNWIND_CODE, struct](struct-unwind-code.md)
##### [Structures d’informations de déroulement chaînées](chained-unwind-info-structures.md)
#### [Procédure de déroulement](unwind-procedure.md)
#### [Gestionnaire propre au langage](language-specific-handler.md)
#### [Assistances de déroulement pour MASM](unwind-helpers-for-masm.md)
##### [Pseudo-opérations brutes](raw-pseudo-operations.md)
##### [Macros MASM](masm-macros.md)
#### [Données de déroulement des définitions en C](unwind-data-definitions-in-c.md)
### [Assembly de fonctions intrinsèques et inline](intrinsics-and-inline-assembly.md)
### [Format d’image](image-format.md)
# [Configurer Visual C++ pour les processeurs ARM](configuring-programs-for-arm-processors-visual-cpp.md)
## [Problèmes courants de migration ARM Visual C++](common-visual-cpp-arm-migration-issues.md)
## [Vue d’ensemble des conventions ABI ARM](overview-of-arm-abi-conventions.md)
## [Vue d’ensemble des conventions ABI ARM64](arm64-windows-abi-conventions.md)
## [Gestion des exceptions ARM](arm-exception-handling.md)
## [Gestion des exceptions ARM64](arm64-exception-handling.md)
# [DLL dans Visual C++](dlls-in-visual-cpp.md)
## [Procédure pas à pas : création et utilisation d’une bibliothèque de liens dynamiques (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)
## [Genres de DLL](kinds-of-dlls.md)
### [DLL non-MFC : vue d’ensemble](non-mfc-dlls-overview.md)
### [DLL MFC normales liées de manière statique à MFC](regular-dlls-statically-linked-to-mfc.md)
### [DLL MFC normales liées de manière dynamique à MFC](regular-dlls-dynamically-linked-to-mfc.md)
### [DLL d’extension de MFC : vue d’ensemble](extension-dlls-overview.md)
## [Forum Aux Questions à propos des DLL MFC](dll-frequently-asked-questions.md)
## [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md)
## [DLL et comportement de la bibliothèque runtime Visual C++](run-time-library-behavior.md)
## [LoadLibrary et AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)
## [GetProcAddress](getprocaddress.md)
## [FreeLibrary et AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)
## [États du module d’une DLL MFC normale liée de manière dynamique à MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)
## [DLL d’extension de MFC](extension-dlls.md)
### [Utilisation de DLL d’extension de MFC de type base de données, OLE et sockets dans des DLL MFC normales](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)
## [Création d’une DLL de ressource uniquement](creating-a-resource-only-dll.md)
## [Ressources localisées dans les applications MFC : DLL satellites](localized-resources-in-mfc-applications-satellite-dlls.md)
## [Importation et exportation](importing-and-exporting.md)
### [Importation dans une application](importing-into-an-application.md)
#### [Importation dans une application à l’aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)
#### [Importation d’appels de fonctions à l’aide de __declspec(dllimport)](importing-function-calls-using-declspec-dllimport.md)
#### [Importation de données à l’aide de __declspec(dllimport)](importing-data-using-declspec-dllimport.md)
#### [Importation à l’aide de fichiers DEF](importing-using-def-files.md)
### [Exportation à partir d’une DLL](exporting-from-a-dll.md)
#### [Exportation à partir d’une DLL à l’aide de fichiers DEF](exporting-from-a-dll-using-def-files.md)
#### [Exportation à partir d’une DLL à l’aide de __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)
#### [Exportation et importation à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)
#### [Exportation de fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)
#### [Exportation de fonctions C à utiliser dans des exécutables en langage C ou C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)
#### [Détermination de la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)
#### [Exportation de fonctions à partir d’une DLL par ordinal plutôt que par nom](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)
### [Importations mutuelles](mutual-imports.md)
### [Importation et exportation de fonctions inline](importing-and-exporting-inline-functions.md)
## [Technologie active et DLL](active-technology-and-dlls.md)
## [Automation dans une DLL](automation-in-a-dll.md)
## [Appel de fonctions de la DLL à partir d’applications Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
# [Fonctions intrinsèques du compilateur et langage assembleur](../intrinsics/TOC.md)
# [Générer du code C/C++ sur la ligne de commande](building-on-the-command-line.md)
## [Procédure pas à pas : compilation d’un programme C++ natif sur la ligne de commande](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)
## [Procédure pas à pas : compiler un programme C sur la ligne de commande](walkthrough-compile-a-c-program-on-the-command-line.md)
## [Procédure pas à pas : compilation d’un programme C++-CLI sur la ligne de commande](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)
## [Procédure pas à pas : compilation d’un programme C++-CX sur la ligne de commande](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)
## [Définir le chemin et les variables d’environnement pour les générations sur la ligne de commande](setting-the-path-and-environment-variables-for-command-line-builds.md)
## [NMAKE, référence](nmake-reference.md)
### [Exécution de NMAKE](running-nmake.md)
#### [NMAKE, options](nmake-options.md)
#### [Tools.ini et NMake](tools-ini-and-nmake.md)
#### [Codes de sortie de NMAKE](exit-codes-from-nmake.md)
### [Contenu d’un makefile](contents-of-a-makefile.md)
#### [NMAKE et les caractères génériques](wildcards-and-nmake.md)
#### [Noms de fichiers longs dans un makefile](long-filenames-in-a-makefile.md)
#### [Commentaires dans un makefile](comments-in-a-makefile.md)
#### [Caractères spéciaux dans un makefile](special-characters-in-a-makefile.md)
#### [Exemple de makefile](sample-makefile.md)
### [Blocs de description](description-blocks.md)
#### [Cibles](targets.md)
##### [Pseudocibles](pseudotargets.md)
##### [Cibles multiples](multiple-targets.md)
##### [Dépendances cumulatives](cumulative-dependencies.md)
##### [Cibles dans des blocs de description multiples](targets-in-multiple-description-blocks.md)
##### [Effets secondaires des dépendances](dependency-side-effects.md)
#### [Dépendants](dependents.md)
##### [Dépendants inférés](inferred-dependents.md)
##### [Chemins de recherche des dépendants](search-paths-for-dependents.md)
### [Commandes dans un makefile](commands-in-a-makefile.md)
#### [Modificateurs de commandes](command-modifiers.md)
#### [Syntaxe des éléments d’un nom de fichier](filename-parts-syntax.md)
#### [Fichiers inline dans un makefile](inline-files-in-a-makefile.md)
##### [Spécification d’un fichier inline](specifying-an-inline-file.md)
##### [Création du texte d’un fichier inline](creating-inline-file-text.md)
##### [Réutilisation de fichiers inline](reusing-inline-files.md)
##### [Fichiers inline multiples](multiple-inline-files.md)
### [NMAKE et les macros](macros-and-nmake.md)
#### [Définition d’une macro NMAKE](defining-an-nmake-macro.md)
##### [Caractères spéciaux dans les macros](special-characters-in-macros.md)
##### [Macros nulles et non définies](null-and-undefined-macros.md)
##### [Où définir des macros](where-to-define-macros.md)
##### [Priorité dans les définitions de macros](precedence-in-macro-definitions.md)
#### [Utilisation d’une macro NMAKE](using-an-nmake-macro.md)
##### [Substitution de macro](macro-substitution.md)
#### [Macros spéciales de NMAKE](special-nmake-macros.md)
##### [Macros de noms de fichiers](filename-macros.md)
##### [Macros récursives](recursion-macros.md)
##### [Macros de commandes et macros d’options](command-macros-and-options-macros.md)
##### [Macros de variables d’environnement](environment-variable-macros.md)
### [Règles d’inférence](inference-rules.md)
#### [Définition d’une règle](defining-a-rule.md)
##### [Chemins de recherche utilisés dans les règles](search-paths-in-rules.md)
#### [Règles en mode batch](batch-mode-rules.md)
#### [Règles prédéfinies](predefined-rules.md)
#### [Règles et dépendants inférés](inferred-dependents-and-rules.md)
#### [Priorité dans les règles d’inférence](precedence-in-inference-rules.md)
### [Directives précédées par un point](dot-directives.md)
### [Prétraitement d’un makefile](makefile-preprocessing.md)
#### [Directives de prétraitement d’un makefile](makefile-preprocessing-directives.md)
#### [Expressions utilisées dans le prétraitement d’un makefile](expressions-in-makefile-preprocessing.md)
##### [Opérateurs de prétraitement d’un makefile](makefile-preprocessing-operators.md)
##### [Exécution d’un programme en prétraitement](executing-a-program-in-preprocessing.md)
## [MSBuild (Visual C++)](msbuild-visual-cpp.md)
### [Vue d’ensemble de MSBuild (Visual C++)](msbuild-visual-cpp-overview.md)
### [Modifications du système de génération](build-system-changes.md)
### [Procédure pas à pas : utilisation de MSBuild pour créer un projet Visual C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
### [Guide pratique pour utiliser des événements de build dans des projets MSBuild](how-to-use-build-events-in-msbuild-projects.md)
### [Guide pratique pour ajouter une étape de génération personnalisée à des projets MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)
### [Guide pratique pour ajouter des outils de génération personnalisés à des projets MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)
### [Guide pratique pour intégrer les outils personnalisés dans les propriétés du projet](how-to-integrate-custom-tools-into-the-project-properties.md)
### [Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](how-to-modify-the-target-framework-and-platform-toolset.md)
# [Configuration des programmes pour Windows XP](configuring-programs-for-windows-xp.md)
# [Référence de la génération C/C++](reference/TOC.md)