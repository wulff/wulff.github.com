# Installér Drupal core

\noindent
Før du begynder at installere Drupal skal du sikre dig at dit webhotel eller din lokale maskine opfylder Drupals minimumskrav til software:

\begin{description}
\item[Webserver] Apache 1.3 eller 2.x, Microsoft IIS
\item[Database] MySQL version 5.0.15 eller nyere, PostgreSQL 8.3 eller nyere
\item[PHP] Til Drupal 7 anbefales PHP 5.3
\end{description}

Dette er kun et udsnit af af systemkravene. Du kan se den til enhver tid gældende liste på følgende adresse:

\shadedlink{http://drupal.org/requirements}

Hvis du installerer dit site på et webhotel hos Gigahost eller på lokal MAMP eller WAMP server behøver du ikke at bekymre dig om systemkravene; du kan installere Drupal~7 uden problemer.

% ----------------------------------------------------------------------------
\section{Installér Drupal på din egen maskine} \label{install-local}

\subsection{Mac OS X}

Gå til \url{http://acquia.com/downloads} og download \emph{Stack installer for Mac OS X}.

%\screenshot{installation/acquia-stack-mac-01.png}{}{acquia-stack-mac-01}

Dobbeltklik på filen for at åbne disk imaget.

\subsection{Linux}

Describe the one-line lamp-server apt-get shortcut?

\subsection{Windows}

Describe how to install Dev Desktop on Windows (including screenshots).

% ----------------------------------------------------------------------------
\section{Installér Drupal på et webhotel} \label{install-webhotel}

Hvis du allerede er klar til at bygge dit første offentligt tilgængelige Drupal-site, eller hvis du gerne vise dine eksperimenter frem, kan du med fordel vælge at installere Drupal på et webhotel i stedet for på din lokale maskine.

I dette afsnit lærer du, hvordan du kan installere Drupal 7 på et webhotel hos \hreffoot{http://gigahost.dk/}{Gigahost}. Fremgangsmåden vil være den samme næsten uanset hvilken af de billige webhoteludbydere du vælger.

Før du går i gang skal kende navnet på databasen som du vil bruge sammen med Drupal~7 samt det brugernavn og den adgangskode som kan bruges til at få adgang til databasen. Hvis du installerer dit site på et webhotel hos Gigahost skal du desuden bruge databaseserverens værtsnavn og portnummer. Du finder begge oplysninger på fanebladet \emph{Adgang} i Gigahost kontrolpanelet.

Vi starter med at hente en kopi af Drupal~7. Du kan altid finde et link til den seneste version på følgende URL, hvor du også kan finde links til populære udvidelsesmoduler og udførlig dokumentation.

\shadedlink{http://drupal.org/start}

Klik på linket \emph{Download Druapl 7.0} for at gå til projektsiden for \emph{Drupal Core}. Projektsiden indeholder links til alle understøttede versioner af Drupal. I skrivende stund er det Drupal~6.x og Drupal~7.x. Siden vi ønsker at installere version 7 skal du klikke på linket \emph{tar.gz} udfor version 7.0 i download-tabellen. Gem filen på dit skrivebord eller et andet sted hvor du nemt kan finde frem til den.

Filen bliver gemt med navnet \texttt{drupal-7.0.tar.gz}. Hvis du bruger Mac eller Linux kan du pakke filen ud blot ved at dobbeltklikke på den. Hvis du bruger Windows kan du downloade en kopi af det gratis program \hreffoot{http://www.7-zip.org/}{7-Zip} og bruge det til at udpakke den downloadede fil.

Når du har udpakket filen skulle du gerne have en mappe med navnet \texttt{drupal-7.0} med samme indhold som på figur \ref{drupal-unpacked}.

\screenshot{installation/drupal-unpacked.png}{Indholdet af Drupal 7-pakken fra drupal.org}{drupal-unpacked}

Nu skal alle de udpakkede filer kopieres til webhotellet. Til det formål har du brug for en FTP-klient. Uanset hvilket operativsystem du bruger er der mange klienter at vælge imellem:

\begin{description}
\item[Mac] \hreffoot{http://cyberduck.ch/}{Cyberduck}, \hreffoot{http://extendmac.com/flow/}{Flow}, \hreffoot{http://www.panic.com/transmit/}{Transmit}
\item[Linux] \hreffoot{http://www.bareftp.org/}{bareFTP}, \hreffoot{http://filezilla-project.org/}{FileZilla}
\item[Windows] FileZilla, \hreffoot{http://winscp.net/}{WinSCP}
\end{description}

For at uploade filerne skal du bruge brugernavnet og adgangskoden til din FTP-konto. Bruger du Gigaghost kan du finde oplysningerne på fanebladet \emph{Adgang} i kontrolpanelet. I dette tilfælde skal vi uploade filerne til serveren \texttt{web18.gigahost.dk} (se figur \ref{ftp-login}).

\screenshot{installation/ftp-login.png}{Login på webhotellet med FTP}{ftp-login}

Før du uploader filerne skal du sikre dig at din FTP-klient viser og overfører skjulte filer. Hvordan det gøres er forskelligt fra klient til klient, men du kan kontrollere det ved at se efter om filen \texttt{.htaccess} bliver vist på listen af filer, som skal overføres (se figur \ref{ftp-overview}).

\screenshot{installation/ftp-overview.png}{Lokale filer klar til at blive overført til webhotellet}{ftp-overview}

Når du overfører filerne skal du sørge for at placere dem i den rigtige mappe på webhotellet. Mappens navn er forskellig fra webhotel til webhotel. Den kan hedde \texttt{html}, \texttt{public} eller noget helt tredje. Bruger du Gigahost skal du overføre filerne til mappen \texttt{www/ditdomæne.dk}.

Hele Drupal~7-mappen fylder omkring 10 MB, så det vil tage nogle minutter for alle filerne er uploadet til dit webhotel. Når alle filerne er blevet overført, er du klar til at køre Drupal's installationsscript.

% ----------------------------------------------------------------------------
\section{Kør Drupals installationsscript}

Når du har installeret et lokalt udviklingsmiljø eller konfigureret dit webhotel er du klar til at installere Drupal. Før vi går i gang skal du sikre dig at du kender adressen på dit lokale site samt brugernavnet og adgangskoden til din database.

Hvis du har fulgt vejledningen i opsætning af et lokalt udviklingsmiljø i det foregående afsnit er adressen på dit lokale site \url{http://d7.local/} og du kan få adgang til databasen \emph{drupal\_7} med brugernavnet \emph{drupal} og adgangskoden \emph{drupal}.

Hvis du installerer Drupal~7 på et webhotel skal du bruge de databaseoplysninger som du har fået fra udbyderen.

Før du kan bruge Drupal skal der oprettes en masse tabeller i databasen. Derfor skal du køre installationsscriptet som leveres med Drupal.

Du starter installationen af Drupal ved at åbne URLen til dit Drupal-site i en browser. Har du installeret Drupal lokalt skal du åbne \texttt{http://localhost/}, ellers skal du åbne \texttt{http://ditdomæne.dk/}.

\screenshot{installation/drupal-profile.png}{Vælg en installationsprofil}{drupal-profile}

På det første trin af installationen (figur \ref{drupal-profile}) skal du vælge en \emph{installationsprofil}. Du kan vælge mellem \emph{Standard} og \emph{Minimal}. Profilen \emph{Standard} er et godt valg hvis du vil hurtigt i gang med at lege med Drupal, eller hvis du vil bygge et simpelt site med en nyhedssektion og nogle få statiske sider. Hvis du skal i gang med at bygge et site fra bunden er det nemmere at starte med profilen \emph{Minimal} og oprette de nødvendige indholdstyper manuelt.

I afsnittet \ref{section-modules-core} på side \pageref{section-modules-core} kan du se hvilke moduler der bliver slået til af de to installationsprofiler. I denne omgang vælger vi installationsprofilen \emph{Standard}, så vi hurtigt kan komme i gang med at bygge vores første Drupal-site.

\screenshot{installation/drupal-language.png}{Vælg sprog for sitet}{drupal-language}

Når du har valgt en installationsprofil skal du vælge hvilket sprog du ønsker at bruge som standardsprog på dit site (se figur \ref{drupal-language}). Som standard kan du kun vælge engelsk. Se afsnit \ref{subsec-danish-install} på side \pageref{subsec-danish-install} for information om hvordan du kan installere Drupal med f.eks.\ dansk som standardsprog.

\screenshot{installation/drupal-database.png}{Konfigurér databasen}{drupal-database}

Derefter kontrollerer installationsscriptet om din webserver og databaseserver opfylder Drupals minimumskrav. Hvis der ikke bliver fundet nogen problemer kan du konfigurere databasen (figur \ref{drupal-database}). Du kan vælge mellem databaserne MySQL, PostgreSQL og SQLite.

Når du har valgt databasetype skal du indtaste databasenavn, brugernavn og adgangskode. Hvis din database ikke ligger på samme server som databaseserveren kan du indtaste et alternativt værtsnavn og databaseport under \emph{Advanced options} (det er bl.a.\ tilfældet hvis du bruger Gigahost, hvor du skal indtaste et databasenavn på formen \texttt{mysqlX.gigahost.dk} og portnummeret \texttt{3306}).

Hvis du bruger den samme database til flere Drupal-sites eller hvis databasen deles af Drupal og Wordpress, kan du indtaste et \emph{table prefix} som bliver tilføjet til alle Drupals tabeller (hvis du bruger d7 som table prefix betyder det f.eks. at \emph{system}-tabellen kommer til at hedde \texttt{d7\_system}).

\screenshot{installation/drupal-batch.png}{Drupal installeres}{drupal-batch}

Derefter sørger installationsscriptet for at installere og konfigurere alle nødvendige moduler (figur \ref{drupal-batch}).

\screenshot{installation/drupal-configure.png}{Konfigurér sitet}{drupal-configure}

Når databasen er konfigureret og installationsprofilens moduler er sat op skal du udfylde basal information om dit site og oprette den første brugerkonto (figur \ref{drupal-configure}). Den første bruger har ubegrænset adgang til hele sitet, så følg anvisningerne for at vælge en sikker adgangskode (i dette eksempel er adgangskoden \texttt{!Drupal7}). Opret en separat admin-konto, som ikke er din dag-til-dag konto. Land/tidszone. Lad de to sidste felter være valgt for at hjælpe dig til at holde dit site opdateret.

\drupalbogwarning{Du bør aldrig bruge den første brugerkonto i dit daglige arbejde med sitet. Brug den kun når du har behov for at opgradere eller installere moduler og temaer. Til dagligt brug kan du oprette en konto med rollen \emph{Administrator}.}

\screenshot{installation/drupal-complete.png}{Installation fuldført}{drupal-complete}

Som sidste trin ændres tilladelserne på settings-filen, så den ikke kan ændres (figur \ref{drupal-complete}). Du kan nu klikke på linket \emph{Visit your new site} for at gå til forsiden af dit nye Drupal-site.

\screenshot{installation/drupal-front.png}{Forsiden af dit nye Drupal-site}{drupal-front}

\drupalboghint{Det er en god idé at læse filen \texttt{INSTALL.txt} som leveres sammen med Drupal. Den indeholder en masse nyttig information om hvordan du installerer Drupal og løser almindeligt forekommende problemer.}

Før du går i gang med at udforske dit nye site bør du sætte et \emph{cron}-job op som kan sørge for at opdatere Drupals søgeindex m.m. Drupal indeholder simpel funktionalitet til at køre periodiske job\footnote{Baseret på funktionalitet fra modulet \emph{Poormanscron}.} (du kan tilpasse indstillingerne på \emph{Configuration $\rightarrow$ Cron}), men du opnår bedre resultater hvis din udbyder tilbyder afvikling af cron-jobs.

\screenshot{installation/gigahost-cron.png}{Opret et nyt periodisk job}{gigahost-cron}

Hvis du bruger Gigahost som webhotel kan du oprette periodiske job direkte i kontrolpanelet. Gå til fanen \emph{Værktøjer}, vælg \emph{Periodiske job} og klik til sidst på \emph{Opret et periodisk job}. Giv dit cron-job et navn og sæt adressen til \texttt{http://ditdomæne.dk/cron.php}. Derefter skal du vælge hvor ofte du ønske at køre jobbet. For langt de fleste sites vil det være passende at vælge \emph{Alle måneder}, \emph{Alle dage} og \emph{Hver time} (se figur \ref{gigahost-cron}).

% ----------------------------------------------------------------------------
\section{Drupal på dansk}

\subsection{Installér Drupal på dansk} \label{subsec-danish-install}

Som du kan se af de forskellige screenshots i forrige afsnit er engelsk standardsproget for Drupals installationsscript. Hvis du ønsker at gennemføre størstedelen af installationen på dansk har du to forskellige muligheder: Du kan enten downloade den danske oversættelse af Drupal manuelt, eller du kan bruge installationsprofilen \emph{Localized Drupal} (du kan læse mere om installationsprofiler i appendix \ref{chapter-profiles} på side \pageref{chapter-profiles}).

\subsubsection{Manuelt}

Den manuelle løsning egner sig bedst hvis du ønsker at installere Drupal med den minimale installationsprofil, som leveres med Drupal.

\begin{enumerate}
\item Gå til \url{http://localize.drupal.org/}
\item Klik på linket \emph{Danish} i tabellen
\item Download oversættelsen af Drupal 7
\item Gem filen i mappen \texttt{profiles/minimal/translations}
\end{enumerate}

Når du kører installationsscriptet har du nu mulighed for at vælge mellem dansk og engelsk som sprog til dit nye Drupal-site.

\subsubsection{Localized Drupal}

Hvis du ønsker at installere Drupal med installationsprofilen \emph{Standard} eller hvis du gerne vil hjælpe til med at oversætte Drupal er det oplagt at bruge installationsprofilen \emph{Localized Drupal}. Profilen indeholder alle tilgængelige oversættelser af Drupal 7, samt alle de værktøjer som du skal bruge for at kunne bidrage til oversættelsesarbejdet. Den seneste version kan hentes fra følgende URL:

\drupalproject{l10n\_install}

\begin{leftbar}
TODO: screenshot fra installscript
\end{leftbar}

\subsection{Installér oversættelser af moduler}

Hvis du har brugt installationsprofilen \emph{Localized Drupal} kan Drupal konfigureres til automatisk at søge efter opdaterede oversættelser af de installerede moduler og temaer. For at få det bedste udbytte bør du kontrollere at indstilllingerne for \emph{Location update}-modulet er fornuftige.

Gå til siden \emph{Configuration $\rightarrow$ Languages $\rightarrow$ Translation updates} og sørg for at indstillingerne svarer til listen nedenfor.

\begin{description}
\item[Update source] Vælg \emph{Remote server only} for kun at hente oversættelser fra den officielle server.
\item[Update mode] Vælg \emph{Edited translations are kept} for at sikre at dine lokale ændringer i oversættelsen ikke bliver overskrevet.
\item[Check for updates] Du kan fint nøjes med at vælge \emph{Weekly}, oversættelserne bliver ikke opdateret dagligt.
\item[Update disable modules] Bør sættes til \emph{Disabled}. Der er ingen grund til at downloade oversættelser af moduler som du ikke bruger.
\end{description}

Når du har gemt indstillingerne kan du gå til \emph{Configuration $\rightarrow$ Translate interface $\rightarrow$ Update} for at søge efter opdaterede oversættelser. Hvis der er tilgængelige opdateringer kan du klikke på \emph{Update translations} for at downloade og installere de nye oversættelser.

\subsection{Hjælp til med oversættelsen} \label{danish-help}

\begin{itemize}
\item l10n\_client
\item l.d.o
\item poedit
\end{itemize}
