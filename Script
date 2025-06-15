// script.js
document.addEventListener('DOMContentLoaded', () => {
    
    // Data for the checklists. In a real app, this would come from a server.
    const procedures = [
        {
            id: 'bonding-prep',
            title: 'Bonding Appointment Prep',
            description: 'Ensure all materials and instruments are ready for the patient.',
            checklist: [
                'Confirm patient chart and planned procedure',
                'Prepare operatory with barrier protection',
                'Lay out bonding tray (mirror, explorer, retractors)',
                'Place etchant, primer, and adhesive on tray',
                'Prepare curing light with protective shield',
                'Select brackets as per treatment plan',
                'Stock cotton rolls, gauze, and saliva ejectors',
                'Review patient allergies and medical alerts'
            ]
        },
        {
            id: 'sterilization',
            title: 'Instrument Sterilization Protocol',
            description: 'Follow SOP for cleaning and sterilizing used instruments.',
            checklist: [
                'Transport contaminated instruments to sterilization area',
                'Perform pre-soak in enzymatic cleaner',
                'Load instruments into ultrasonic cleaner',
                'Rinse and dry instruments thoroughly',
                'Package instruments in sterilization pouches',
                'Load and operate autoclave according to manufacturer settings',
                'Log sterilization cycle and store sterile packages'
            ]
        },
        {
            id: 'debond-prep',
            title: 'Debonding Appointment Prep',
            description: 'Prepare for bracket removal and final impressions.',
            checklist: [
                'Prepare debonding pliers and other removal tools',
                'Set up for polishing (pumice, prophy angle)',
                'Prepare impression trays and alginate material',
                'Have retainer case ready for patient',
                'Ensure final patient photos are ready to be taken'
            ]
        }
    ];

    const gridContainer = document.querySelector('.procedure-grid');
    const modal = document.getElementById('checklist-modal');
    const modalBody = document.getElementById('modal-body');
    const closeButton = document.querySelector('.close-button');

    // Create the procedure cards on the main page
    function renderCards() {
        const cardGrid = document.createElement('div');
        cardGrid.className = 'card-grid';
        procedures.forEach(proc => {
            const card = document.createElement('div');
            card.className = 'procedure-card';
            card.dataset.id = proc.id;
            card.innerHTML = `
                <h3>${proc.title}</h3>
                <p>${proc.description}</p>
            `;
            card.addEventListener('click', () => openModal(proc));
            cardGrid.appendChild(card);
        });
        gridContainer.appendChild(cardGrid);
    }

    // Open the checklist modal
    function openModal(procedure) {
        modalBody.innerHTML = `
            <h2>${procedure.title}</h2>
            <ul class="checklist">
                ${procedure.checklist.map((item, index) => `
                    <li class="checklist-item">
                        <input type="checkbox" id="item-${index}">
                        <label for="item-${index}">${item}</label>
                    </li>
                `).join('')}
            </ul>
            <div class="completion-message" style="display: none;">
                <h3>Amazing! Procedure prepped.</h3>
            </div>
        `;
        modal.style.display = 'flex';
        addCheckboxListeners(procedure);
    }

    // Add logic for checking items and showing completion message
    function addCheckboxListeners(procedure) {
        const checkboxes = modal.querySelectorAll('input[type="checkbox"]');
        const completionMessage = modal.querySelector('.completion-message');

        checkboxes.forEach(checkbox => {
            checkbox.addEventListener('change', () => {
                checkbox.parentElement.classList.toggle('completed', checkbox.checked);
                const allChecked = Array.from(checkboxes).every(cb => cb.checked);
                completionMessage.style.display = allChecked ? 'block' : 'none';
            });
        });
    }

    // Close the modal
    function closeModal() {
        modal.style.display = 'none';
    }

    closeButton.addEventListener('click', closeModal);
    modal.addEventListener('click', (e) => {
        if (e.target === modal) {
            closeModal();
        }
    });

    renderCards();
});
