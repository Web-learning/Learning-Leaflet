
function CreditBottomRight(author, licenseUrl, licenseName = "", minWidth = 600) {
    const credit = document.createElement("div");

    credit.innerHTML = `© ${author} · <a href="${licenseUrl}" target="_blank" rel="noopener">${licenseName}</a>`;

    Object.assign(credit.style, {
        position: "fixed",
        bottom: "10px",
        right: "10px",
        background: "rgba(255,255,255,0.85)",
        padding: "4px 8px",
        fontSize: "12px",
        borderRadius: "4px",
        boxShadow: "0 0 5px rgba(0,0,0,0.3)",
        zIndex: 1000,
        fontFamily: "sans-serif"
    });

    // style link
    const styleLink = () => {
        const a = credit.querySelector("a");
        if (a) {
            a.style.color = "#0078A8";
            a.style.textDecoration = "none";
        }
    };

    function updateVisibility() {
        credit.style.display = window.innerWidth < minWidth ? "none" : "block";
    }

    window.addEventListener("resize", updateVisibility);

    document.body.appendChild(credit);
    styleLink();
    updateVisibility();

    return credit;
}

// Example usage
CreditBottomRight(
    "by Derek Moore", "http://www.weblearning.co.za", "Creative Commons"
);

